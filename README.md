# roars-writing

A [Cursor Agent Skill](https://cursor.com/docs/context/skills) that encodes **ROARS lab** writing and formatting rules from [`lab-manual.typ`](https://github.com/dynaroars/phd-cs-us/blob/main/lab-manual.typ).

## What it does

When you edit ROARS Typst guides, LaTeX papers, rebuttals, or slides, the agent applies:

- **Typst** — preamble (11pt, 1in margins, justified text), green callouts, `#highlight` / `#rect` / `#link`, section labels
- **Papers** — single `paper.tex` + `paper.bib`, `authorYearFirstWordOfTitle` bib keys, section **write order** (Overview → Experiments → Techniques → Related Work → Conclusion → Introduction last), negative results, related-work diff paragraphs
- **Rebuttals & slides** — thank reviewers first; numbered slides (~1/min); motivation over heavy technical slides

Full rules live in `reference.md`; worked examples in `examples.md`.

## Install

### Cursor (personal — all projects)

```bash
git clone git@github.com:thanhlexyz/roars-writing-skill.git ~/.cursor/skills/roars-writing
```

Restart Cursor or start a new agent chat so the skill is indexed.

### Cursor (one project only)

```bash
git clone git@github.com:thanhlexyz/roars-writing-skill.git .cursor/skills/roars-writing
```

Run from your project root (creates `.cursor/skills/roars-writing/`).

### Update

```bash
cd ~/.cursor/skills/roars-writing && git pull
```

## Use

- **Auto** — Cursor can apply the skill when you work on matching files (`lab-manual.typ`, `advising.typ`, `demystify.typ`, `paper.tex`, etc.).
- **Explicit** — attach or mention `@roars-writing` in chat.

## Files

| File | Role |
|------|------|
| `SKILL.md` | Agent workflow and checklist |
| `reference.md` | Complete rules from `lab-manual.typ` |
| `examples.md` | Before/after Typst, LaTeX, bib keys, section order |

## Source

Rules are derived from [dynaroars/phd-cs-us](https://github.com/dynaroars/phd-cs-us) `lab-manual.typ`. Update the skill when that file changes.

## Related skills

- **avoid-ai-writing** — strip AI-isms after drafting
- **research-paper-writing** — ML paper reviewer polish beyond lab-manual scope
