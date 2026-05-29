# ROARS Writing — Reference

Source of truth: `lab-manual.typ` in [phd-cs-us](https://github.com/dynaroars/phd-cs-us). Every rule below is taken from that file.

---

## Typst preamble (`lab-manual.typ`)

Required settings for ROARS lab manuals and matching guides (`advising.typ`, etc.):

```typst
#set heading(numbering: "1.")
#set text(lang: "en", size: 11pt)
#set list(indent: 1em)
#set enum(indent: 1em)
#set page(margin: 1in)
#set par(justify: true)
#show ref: set text(fill:blue)
#show link: set text(fill:blue)
#show link: underline
#show quote: set text(style: "italic")
#show heading: set block(above: 1.4em, below: 1em)
#show title: set text(size: 17pt)
#show title: set align(center)
```

Optional in other guides but present in `lab-manual.typ`:

```typst
#let dark-green = rgb("#006400")
#let light-green = rgb("#d4f1d4")

// Inline code
#show raw.where(block: false): it => box(fill: rgb("#f0f0f0"), inset: (x: 2pt), radius: 2pt, it)

// Code blocks
#show raw.where(block: true): it => block(fill: rgb("#f0f0f0"), inset: 10pt, radius: 4pt, width: 100%, it)
```

**Do not change** these when editing content unless the user explicitly requests a layout change.

### Title page (`lab-manual.typ`)

- Full-page `#box(stroke: (paint: dark-green, thickness: 3pt), inset: 2em, ...)`
- Title 32pt bold, author 18pt bold, affiliation 14pt
- `#pagebreak()` before body

### Document structure

1. Title page (lab-manual style) or `#title[...]` + centered author (advising style)
2. Green intro `#block(fill: light-green, stroke: dark-green, inset: 1em)[...]`
3. `#outline()` then `#pagebreak()`
4. Body sections `=`, `==`, `===`
5. `#pagebreak()` between major parts when the source file does
6. Appendices: `#set heading(numbering: "A.1")` then `= Appendix Title`

### Typst markup conventions

| Construct | Use |
|-----------|-----|
| `#highlight[text]` | Mandatory expectations, key terms readers must not miss |
| `#block(fill: light-green, stroke: dark-green, inset: 1em)[...]` | Intro, warnings (e.g. Debian packages) |
| `#rect[...]` | Notes, caveats, email templates, addresses |
| `#link("url")[text]` | External links; ROARS links often `https://roars.dev` |
| `#link(<label>)` | Internal cross-refs to labeled content |
| `<label>` on heading | e.g. `== File Organization <sec:file-organization>` |
| `@meals` / `@sec:id` | Reference labeled sections |
| `#quote[...]` | Quoted speech; italic via `#show quote` |
| `#figure(image(...), caption: [...])` | Figures with caption |
| `+` / `-` lists | Steps, specs, channels; indent 1em per `#set list/enum` |
| `_italic_` / `*bold*` | Emphasis in body (bold for channel names like `#stats`) |
| `` `code` `` | Commands, filenames, tools — uses gray raw styling |

**Heading levels:** `=` chapter, `==` section, `===` subsection. Do not skip levels.

**Dashes in Typst:** `--` → en-dash; `---` → em-dash when needed.

---

## File organization

> Everyone has their own way… Below is **my approach**. If you're my student and write papers with me, **I expect you follow this approach**.

### Collaboration exception

Use `#rect[Note that ...]` pattern: if collaborating and **not** the lead, follow the lead's organization. If **we** lead the paper, follow the rules below.

### Version control

- **Git** (e.g. GitHub) for all papers — essential for collaboration.
- Even with Overleaf, **link to a GitHub repo**.

### Directory layout (minimal)

| Path | Rule |
|------|------|
| `paper.tex` | **Single** TeX file for the entire paper (intro, eval, related — all in one file). |
| `paper.bib` | **Single** bib file. |
| `figures/` | All figures; if only a few, may live beside `paper.tex`. |

**Naming variants:** `paper-cacm26.tex` OK — still one file per paper/venue.

**Do not:**

- Split into `intro.tex`, `sections/related.tex`, etc. (ROARS preference: search/replace and flow without file switching).
- Symlink `~/myrefs.bib` or `~/myfigs/` — **copy** bib and figures into the paper directory so the project is **self-contained** for sharing and review.

### Bibliography keys

Convention: `authorYearFirstWordOfTitle`

- Example: Duong 2020 "Verifying …" → `duong2020verifying`
- Matches Google Scholar export — easy copy/paste.
- Same author + year collision: `duong2026verifying`, `duong2026verifying2`, …

### LaTeX equivalent defaults

When creating `paper.tex` from scratch for ROARS papers:

```latex
\documentclass[11pt]{article}
\usepackage[margin=1in]{geometry}
```

Use the project's existing preamble if the file already exists.

---

## Research paper writing order

Reference paper: [Dynaplex (OOPSLA'21)](https://roars.dev/pubs/ishimwe2021dynaplex.pdf).

Write sections in this order (section numbers are typical placement, not writing order):

### 1. Overview (often §2) — write **first**

- Start here, not Introduction.
- Include an **illustrative or concrete example**.
- After Overview (+ skimming Intro), readers should understand the approach.
- **Goal:** readers/reviewers can decide if they like the work after this part.
- Add an **overview figure** (architecture / main components).
- Optional: background and definitions (e.g. Dynaplex §2.2).

Contents typically:

- Architecture/overview figure (e.g. Fig 1)
- Motivation / walkthrough example (what the tool does on an input, what it outputs)
- Main definitions and background (optional)

### 2. Experimental (often §4) — write **second**

- Some implementation details (tools, libraries).
- **Research Questions (RQs)** — e.g. accuracy, efficiency, comparison to baselines.
- **Benchmarks** — what programs, why they fit the RQs.
- **Experiment setup** — machine specs, how runs were executed (repeats, means, etc.).
- **Results and analysis** per RQ.
- **Report negative results** — if benchmark X fails, explain why (factors Y, Z).

### 3. Algorithm / Techniques (often §3)

### 4. Related Work (often §5)

- Subsections as needed.
- After each related-work subsection: **new paragraph** on how **this** work differs / relates.

### 5. Conclusion (often §6)

- Must be **conclusion**, not **summary**.
- Future work allowed here.

### 6. Introduction (§1) — write **last**

By then you have contributions, results, and gaps clear. Typically includes:

1. Problem and why it matters (what we accomplish if solved).
2. Existing work — why challenging / insufficient.
3. Proposed approach — how it addresses limitations; other benefits.
4. Brief results summary.

---

## Rebuttal

1. **Thank-you note first** — thank reviewers for time and feedback.
2. Do this even if reviews are harsh.

---

## Presentation

| Rule | Detail |
|------|--------|
| Title slide | Paper title, authors (**highlight/underline presenter**), affiliations, venue, date |
| Number slides | So audience can cite "on slide 10…" |
| Timing | **~1 slide per minute** |
| Technical depth | **Avoid** heavy formulae, code, algorithms unless necessary |
| Goal | Motivation and high-level ideas — get people to **talk to you and read the paper** |
| Tooling | [Optional] LaTeX/Beamer for consistency with paper |

---

## Voice (lab-manual style)

- **First person** for lab policy and expectations.
- **`#highlight[I expect ...]`** for non-negotiable student requirements.
- **`#rect[...]`** for exceptions (collaboration, templates).
- **Concrete examples** — link to real papers (`Dynaplex`), servers (Boba, Pizza), channels (`#stats`).
- **Direct negatives** — "DO NOT", "will not enjoy", spelled out consequences.
- **Honest scope** — neutral/generic LoR if writer doesn't know student well.

---

## Reverse outlining

Use when flow is weak:

1. Section thesis in one sentence.
2. Topic sentence per paragraph.
3. Evidence under each (fact, link, example).
4. Cut or merge unmapped paragraphs.

---

## Revision checklist

### Typst (`lab-manual.typ`)

- [ ] Preamble block matches spec above
- [ ] `dark-green` / `light-green` on callouts
- [ ] Code raw styling for inline and block
- [ ] Links blue + underlined; refs blue
- [ ] Labels on cross-referenced sections
- [ ] `#pagebreak()` placement preserved when restructuring

### LaTeX paper

- [ ] Single `paper.tex`, single `paper.bib`, self-contained figures
- [ ] Bib keys `authorYearFirstWordOfTitle`
- [ ] Written in order: Overview → Experiments → Techniques → Related Work → Conclusion → Intro
- [ ] Overview: example + figure; Experiments: RQs, negatives; Related Work: diff paragraph each subsection
- [ ] Conclusion ≠ summary

### Rebuttal & slides

- [ ] Rebuttal thanks reviewers upfront
- [ ] Slides numbered; ~1/min; low technical density
