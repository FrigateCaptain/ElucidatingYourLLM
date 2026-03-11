# Generated Documents — Creating DOCX/ODT

**Domain rule.** Apply when programmatically creating text documents.

Globs: `**/*.docx, **/*.odt`

---

## Generated Document Files Rules [MANDATORY]

When programmatically creating `.docx`, `.odt`:

1. **Document language [MANDATORY]**: Set the language to match the content language.
   - Detect automatically (all text in Russian → `ru-RU`, English → `en-US`)
   - Mixed-language content — ask the user
   - Do not rely on the library's default language (python-docx defaults to `en-US`)

2. **For `.docx` (python-docx)**: Set the language in three places:
   - `docDefaults` → `rPrDefault` → `rPr` → `w:lang`
   - `themeFontLang` in `settings`
   - `Normal` style → `rPr` → `w:lang`

**Reason**: Wrong language → spell check underlines the entire text as errors.
