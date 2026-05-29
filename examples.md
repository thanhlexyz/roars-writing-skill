# ROARS Writing — Examples

---

## Example 1: Policy with `#highlight` and `#rect` caveat

```typst
Everyone has their own way of organizing files and writing papers. Below is
my approach that has worked well for me over the years. If you're my student
and write papers with me, #highlight[I expect you follow this approach] so
that we can be on the same page and work efficiently together.

#rect[Note that if we collaborate with others, we can adapt how we write and
organize files as needed. Typically, the main group lead will decide how to
organize things and the rest of us will follow their lead.]
```

---

## Example 2: Bib key convention

| Paper | Key |
|-------|-----|
| Duong 2020 "Verifying Neural Networks..." | `duong2020verifying` |
| Second Duong 2026 verifying paper | `duong2026verifying2` |

**Wrong:** `Duong2020`, `ref47`, `paper1`

---

## Example 3: Paper section order mistake

**Wrong writing order:** Introduction → Method → Experiments → Related Work → Conclusion

**ROARS order:** Overview → Experiments → Techniques → Related Work → Conclusion → **Introduction last**

**Why:** Intro needs final contributions, results, and gap analysis from the other sections.

---

## Example 4: Overview section content

```typst
== Overview <sec:overview>

We motivate #highlight[Dynaplex] with the program in @fig:motivating-example.
After this section, readers should understand what the tool produces and why
the architecture in @fig:architecture is organized as shown.

#figure(
  image("figures/overview.pdf", width: 100%),
  caption: [Architecture of Dynaplex.],
) <fig:architecture>
```

---

## Example 5: Related Work closing paragraph

After each related-work subsection, add a paragraph like:

```latex
Our work differs from X in that we handle Y automatically, whereas X requires
manual annotation. Unlike Z, we do not assume access to source code.
```

---

## Example 7: Rebuttal opening

```latex
We thank the reviewers for their thoughtful feedback and time spent reviewing
our submission. Below we address each comment.
```

---

## Example 8: Presentation slide discipline

**Avoid:** Slide full of inference rules and 40 lines of pseudocode.

**Prefer:** One motivating example, architecture figure, result headline — aim for **~1 slide/minute**, **numbered slides**, presenter name **underlined** on title slide.

---

## Example 9: File layout

```
paper_gentree/
  paper.tex          % entire paper, single file
  paper.bib          % copied from scholar export, not ~/myrefs.bib symlink
  figure/
    overview.pdf
    results.pdf
```

**Not ROARS style:**

```
sections/intro.tex
sections/eval.tex
~/shared/refs.bib -> paper.bib
```
