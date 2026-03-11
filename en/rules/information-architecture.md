# Information Architecture — Information Structure and Content Quality

---

## Information Architecture [MANDATORY]

### Principle
Eliminate ambiguities, duplicates, inconsistencies, and unclear sources.

### Canonical Definitions System [CANONICAL]

**Rule**: Every statement must have a traceable source.

- **Single Source of Truth**: Each concept has ONE canonical version
- **[CANONICAL] label**: Place in the source document where the information was first established
- **[REF:] links**: All other mentions use `[REF: folder/file.md#section]`
- **Exact repetition**: Use identical wording when referencing
- **Explicit adaptation**: When modifying, mark as `[ADAPTED from file.md: "original" → "adaptation"]`

### Source Labels

- **[CANONICAL]** — authoritative definition
- **[CONFIRMED: source]** — verified information
- **[PLACEHOLDER: owner]** — information to be filled in
- **[REF: path]** — cross-reference

### Traceability Requirements

- **No Orphan Statements**: Every statement must be traceable to a source
- **Clear Attribution**: State where the information comes from — notes, research, calculations

### Anti-Hallucination Rules

- **Remove unconfirmed content** — only information from reliable sources
- **Use real data** — concrete metrics from records
- **Source for every statement** — `[CANONICAL]` or `[REF:]`
- **Mark placeholders** — `[PLACEHOLDER: owner]`
- **Date everything** — include "Last updated" timestamps
- **Maintain traceability** — update all references when sources change

---

## Content Quality Standards [MANDATORY]

1. **Remove hallucinated content** — only verified information
2. **Use real data** — metrics from actual operations
3. **Source for every statement** — `[CANONICAL]` or `[REF:]`
4. **Mark placeholders** — `[PLACEHOLDER: owner]`
5. **Cross-references** — link documents via `[REF:]`
6. **Date everything** — "Last updated" timestamps
7. **Maintain traceability** — update references when sources change
