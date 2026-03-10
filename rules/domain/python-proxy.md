# Python Proxy — Обработка прокси в Python-скриптах

**Опциональное доменное правило.** Применять если в системе используется VPN/прокси.

Globs: `**/*.py`

---

## Network Proxy in Python Scripts [MANDATORY]

**При создании любого Python-скрипта, выполняющего HTTP/HTTPS-запросы к внешним API** — добавить в начало скрипта (до импорта сетевых библиотек) блок обработки прокси.

### Контекст

На машине может быть активен прокси (HTTP или SOCKS). Два типа:
- **HTTP-прокси** (`http://127.0.0.1:<port>`) — httpx/requests поддерживают
- **SOCKS-прокси** (`socks://127.0.0.1:<port>`) — httpx **не поддерживает** схему без версии. Выдаёт `ValueError: Unknown scheme for proxy URL`

### Правило [MANDATORY]

**НЕ удалять** `http://`-прокси — они могут быть нужны для доступа к API.

**Конвертировать** `socks://` → `socks5://`:

```python
import os
for _var in ("http_proxy", "https_proxy", "HTTP_PROXY", "HTTPS_PROXY", "ALL_PROXY", "all_proxy"):
    val = os.environ.get(_var, "")
    if val.startswith("socks://"):
        os.environ[_var] = val.replace("socks://", "socks5://", 1)
```

**Применяется к скриптам, обращающимся к внешним API:**
- AI SDK: `groq`, `openai`, `anthropic`, `google-genai` и др.
- HTTP-библиотеки: `requests`, `httpx`, `aiohttp`

**Не применяется к:**
- Скриптам без сетевого доступа
- Локальным вызовам (localhost, 127.0.0.1)

---

## SOCKS Proxy Compatibility [MANDATORY]

**Два сценария — два решения:**

**Сценарий A: загрузка локальных моделей** (huggingface_hub, Whisper, ONNX и т.п.)
- Прокси не нужен — использовать `_no_proxy()` контекстный менеджер:

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

**Сценарий B: вызовы внешних API** (Groq, OpenAI, Anthropic и т.п.)
- HTTP-прокси оставить, только конвертировать `socks://` → `socks5://`
- Смотри раздел «Network Proxy in Python Scripts» выше
