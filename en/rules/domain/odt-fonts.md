# ODT Fonts — Fonts in LibreOffice Documents

**Domain rule.** Apply when creating and editing `.odt` files.

Globs: `**/*.odt`

---

## Formatting Rules [MANDATORY]

- Default base font: **Roboto Light**, 12 pt.
- Headings and text styles (Heading 1–6, Text Body, Standard) inherit Roboto Light; change the font only on explicit user request.
- If Roboto Light is not available — install it or temporarily use Roboto Regular and flag the task.
- When creating/updating ODT, verify that `styles.xml` default paragraph and Heading styles use `style:font-name="Roboto Light"`.
- Do not embed the font in the file without a direct request.
- Note in the report that the default font has been set to Roboto Light.
