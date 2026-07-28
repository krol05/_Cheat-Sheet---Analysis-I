# Analysis I — exam recipe sheet (ETHZ, D-INFK)

A 10-page A4-landscape cheat sheet for the ETHZ Analysis I exam. Every entry is written
to answer "I have **this** question → do **this**", so it is usable under time pressure
rather than being a condensed textbook.

## Build

```bash
latexmk -pdf main.tex
```

`main.pdf` is committed, so you can grab the rendered sheet without a TeX install.

## Structure

`main.tex` holds the preamble (fonts, palette, box styles, page furniture) and `\input`s
one file per section:

| File | Section |
|---|---|
| `00-howto.tex` | legend and the "the task says… → jump to" index |
| `01-foundations.tex` | sup/inf, induction, estimates, vectors |
| `02-complex.tex` | complex numbers and polynomials |
| `03-sequences.tex` | sequences |
| `04-series.tex` | series |
| `05-powerseries.tex` | power series and Taylor |
| `06-functions.tex` | limits, continuity, IVT/EVT |
| `07-functionsequences.tex` | sequences of functions |
| `08-derivatives.tex` | derivatives and applications |
| `09-integration.tex` | integration |
| `10-ode.tex` | differential equations |
| `11-proofs.tex` | standard proofs from the lecture |
| `12-examblock.tex` | true/false scan index and model solutions |
| `13-tables.tex` | lookup tables |

## Conventions

Content goes in one of six boxes, each with its own colour:

| Macro | Box | Use for |
|---|---|---|
| `\R{title}{…}` | RECIPE (green) | a step-by-step procedure |
| `\D{title}{…}` | DEF (orange) | a definition an exercise actually needs |
| `\F{title}{…}` | FACT (gold) | a theorem you may cite |
| `\E{title}{…}` | EXAMPLE (blue) | a worked example |
| `\X{title}{…}` | TRAP (red) | a pitfall or a multiple-choice trap |
| `\T{title}{…}` | TABLE (violet) | a lookup table |

Inside a box: `\hd{…}` for a run-in heading, `\de{…}` for the German exam wording,
`\warn` for an inline warning, and the `rcp` / `bul` list environments.

True/false verdicts are colour-linked to the claim they judge: `\claimT{…}` / `\claimF{…}`
in prose, `\stT{…}` / `\stF{…}` for the statement cell of a true/false table. The green
`T` / red `F` marker stays visible either way.

Navigation: a contents strip along the top edge of every page lists all 13 sections with
their page numbers (the ones live on that page in dark), matching the coloured edge tabs
in the outer margin.

## Rules that keep it at 10 pages

- The whole body is **one** continuous `multicols{3}` — no `\clearpage`, no nesting.
- `\raggedcolumns` is load-bearing; see the comment block at the top of `main.tex`.
- Keep every box well under a third of a column. Boxes are `unbreakable`, so a tall one
  strands the rest of its column. Splitting an over-long table into two boxes is the fix;
  making boxes `breakable` is not — it costs two pages.
- Cross-references always go through `\label` / `\ref`, never hard-coded numbers.
- If it overflows, in this order: fill reclaimed whitespace → margins → font size →
  only then cut content.
