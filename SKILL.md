---
name: roars-writing
description: Drafts and revises documents following ROARS lab writing rules and Typst/LaTeX conventions from lab-manual.typ. Covers Typst preamble, green callouts, file organization, research-paper section order, rebuttals, and presentations. Use when editing lab-manual.typ, advising.typ, demystify.typ, paper.tex, roars.dev docs, or any ROARS-style guide or paper.
---

# ROARS Writing

Apply **all** rules from `lab-manual.typ` in the `phd-cs-us` repo. When editing that file or matching ROARS lab docs, read [reference.md](reference.md) and verify every rule below.

## When to use other skills

| Task | Skill |
|------|-------|
| AI-ism cleanup | `avoid-ai-writing` |
| ML paper reviewer polish (beyond lab-manual order) | `research-paper-writing` |

## Workflow

### 1. Identify document type

| Type | Rules section in [reference.md](reference.md) |
|------|-----------------------------------------------|
| Typst lab/guide (`.typ`) | Typst preamble & markup |
| LaTeX paper (ROARS) | File organization + paper section order |
| Rebuttal | Rebuttal |
| Slides | Presentation |
| Other prose | Voice principles |

### 2. Typst edits (`lab-manual.typ` and siblings)

Before delivering Typst changes:

1. **Preserve preamble** — do not alter `#set` / `#show` unless the user asks (see reference for required values).
2. **Use lab markup** — `#highlight`, `#block(fill: light-green, stroke: dark-green, ...)`, `#rect[...]`, `#link`, labels `<id>`, `@meals`-style refs.
3. **Layout** — 11pt English, 1in margin, justified body, blue underlined links, italic `#quote`.
4. **Structure** — `= ` / `== ` / `=== ` hierarchy; `#outline()` + `#pagebreak()`; appendix `A.1` numbering when applicable.

Full preamble template and color constants: [reference.md#typst-preamble-lab-manualtyp](reference.md#typst-preamble-lab-manualtyp).

### 3. LaTeX / paper edits

For ROARS lab papers:

1. **Files** — prefer single `paper.tex`, single `paper.bib`, `figures/`; self-contained (no symlinked shared bib/figs).
2. **Bib keys** — `authorYearFirstWordOfTitle` (e.g. `duong2020verifying`); suffix `2` if same author/year collision.
3. **Section order** — Overview → Experiments → Techniques → Related Work → Conclusion → Introduction (Intro last).
4. **Content rules** — illustrative Overview with figure; report negative results; Related Work ends each subsection with how this work differs; Conclusion is not a summary.

Details: [reference.md#research-paper-writing-order](reference.md#research-paper-writing-order).

### 4. Prose pass

- Direct expectations: `#highlight[I expect you follow this approach]` style when stating lab policy.
- Lead with the point; use `#rect[Note that ...]` for caveats (e.g. collaboration exceptions).
- Lists OK for steps, file trees, server specs, reimbursement bullets — not for policy that should read as prose.

### 5. Checklist (run before delivery)

```
Typst / guide
- [ ] Preamble matches lab-manual.typ (#set text 11pt, margin 1in, justify, link/quote/heading shows)
- [ ] Green intro/warning blocks use dark-green #006400 and light-green #d4f1d4
- [ ] #highlight only for must-notice terms (not decoration)
- [ ] Section labels on headings that are cross-referenced

LaTeX paper (ROARS lab)
- [ ] Single paper.tex + paper.bib (+ figures/) unless collaborating under another lead
- [ ] Bib keys authorYearFirstWordOfTitle
- [ ] Section order: Overview → Experiments → Techniques → Related Work → Conclusion → Intro
- [ ] Overview has concrete example + overview figure; Experiments include negative results

Rebuttal / slides
- [ ] Rebuttal opens with thank-you to reviewers
- [ ] Slides numbered; ~1 slide/minute; motivation over formulae/code unless necessary
```

## Output conventions

- **Typst**: return valid Typst fragments; preserve indentation inside section bodies.
- **LaTeX**: match existing document class and packages; do not split into multi-file structure unless user requests.
- Do not change policy meaning or soften `#highlight[I expect ...]` requirements.

## Examples

[examples.md](examples.md)

## Full rule reference

[reference.md](reference.md) — authoritative copy of every `lab-manual.typ` writing and format rule.
