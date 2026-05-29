# roars-writing

An agent skill that encodes **ROARS lab** writing and formatting rules from [`lab-manual.pdf`](https://github.com/dynaroars/phd-cs-us/blob/main/lab-manual.pdf).

## What it does

When you edit papers, rebuttals, or slides, the agent applies:

- **Papers** — single `paper.tex` + `paper.bib`, `authorYearFirstWordOfTitle` bib keys, section **write order** (Overview → Experiments → Techniques → Related Work → Conclusion → Introduction last), negative results, related-work diff paragraphs
- **Rebuttals & slides** — thank reviewers first; numbered slides (~1/min); motivation over heavy technical slides

Full rules live in `reference.md`; worked examples in `examples.md`.

## Install

```bash
git clone git@github.com:thanhlexyz/roars-writing-skill.git ~/.skills/roars-writing
```

Restart Cursor or start a new agent chat so the skill is indexed.

Run from your project root (creates `.cursor/skills/roars-writing/`).


## Files

| File | Role |
|------|------|
| `SKILL.md` | Agent workflow and checklist |
| `reference.md` | Complete rules from `lab-manual.typ` |
| `examples.md` | Before/after Typst, LaTeX, bib keys, section order |

## Source

Rules are derived from [dynaroars/phd-cs-us](https://github.com/dynaroars/phd-cs-us) `lab-manual.pdf`.
Update the skill when that file changes.
