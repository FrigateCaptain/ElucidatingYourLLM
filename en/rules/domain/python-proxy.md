# Python Proxy — Handling Proxies in Python Scripts

**Optional domain rule.** Apply when the system uses a VPN/proxy.

Globs: `**/*.py`

---

## Network Proxy in Python Scripts [MANDATORY]

**When creating any Python script that makes HTTP/HTTPS requests to external APIs** — add a proxy handling block at the top of the script (before importing networking libraries).

### Context

The machine may have an active proxy (HTTP or SOCKS). Two types:
- **HTTP proxy** (`http://127.0.0.1:<port>`) — httpx/requests support this
- **SOCKS proxy** (`socks://127.0.0.1:<port>`) — httpx **does not support** the versionless scheme. Throws `ValueError: Unknown scheme for proxy URL`

### Rule [MANDATORY]

**DO NOT remove** `http://` proxies — they may be needed for API access.

**Convert** `socks://` → `socks5://`:

```python
import os
for _var in ("http_proxy", "https_proxy", "HTTP_PROXY", "HTTPS_PROXY", "ALL_PROXY", "all_proxy"):
    val = os.environ.get(_var, "")
    if val.startswith("socks://"):
        os.environ[_var] = val.replace("socks://", "socks5://", 1)
```

**Applies to scripts that call external APIs:**
- AI SDKs: `groq`, `openai`, `anthropic`, `google-genai`, etc.
- HTTP libraries: `requests`, `httpx`, `aiohttp`

**Does not apply to:**
- Scripts without network access
- Local calls (localhost, 127.0.0.1)

---

## SOCKS Proxy Compatibility [MANDATORY]

**Two scenarios — two solutions:**

**Scenario A: loading local models** (huggingface_hub, Whisper, ONNX, etc.)
- Proxy is not needed — use the `_no_proxy()` context manager:

```python
import contextlib, os

_PROXY_ENV_VARS = [
    "HTTP_PROXY", "HTTPS_PROXY", "ALL_PROXY",
    "http_proxy", "https_proxy", "all_proxy",
]

@contextlib.contextmanager
def _no_proxy():
    """Temporarily clear proxy env vars for local model loading."""
    saved = {k: os.environ.pop(k, None) for k in _PROXY_ENV_VARS}
    try:
        yield
    finally:
        for k, v in saved.items():
            if v is not None:
                os.environ[k] = v

with _no_proxy():
    model = WhisperModel(...)
```

**Scenario B: external API calls** (Groq, OpenAI, Anthropic, etc.)
- Keep HTTP proxies, only convert `socks://` → `socks5://`
- See the "Network Proxy in Python Scripts" section above
