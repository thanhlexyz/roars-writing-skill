# ROARS Writing — Reference

Source of truth: `lab-manual.pdf` in [phd-cs-us](https://github.com/dynaroars/phd-cs-us).
Every rule below is taken from that file.


---

## File organization

> Everyone has their own way… Below is **my approach**. If you're my student and write papers with me, **I expect you follow this approach**.

### Collaboration exception

Use `#rect[Note that ...]` pattern: if collaborating and **not** the lead, follow the lead's organization.
If **we** lead the paper, follow the rules below.

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


### LaTeX paper

- [ ] Single `paper.tex`, single `paper.bib`, self-contained figures
- [ ] Bib keys `authorYearFirstWordOfTitle`
- [ ] Written in order: Overview → Experiments → Techniques → Related Work → Conclusion → Intro
- [ ] Overview: example + figure; Experiments: RQs, negatives; Related Work: diff paragraph each subsection
- [ ] Conclusion ≠ summary

### Rebuttal & slides

- [ ] Rebuttal thanks reviewers upfront
- [ ] Slides numbered; ~1/min; low technical density
