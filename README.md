# Recipe Site Traffic — Tasty Bytes

DataCamp Data Scientist Professional Certificate, practical exam. Tasty Bytes hand-picks one
recipe for the site's homepage each day; a popular pick lifts traffic to the rest of the site
by up to 40%. This project predicts which recipes will draw that traffic.

## The result

Of the recipes the model recommends, about **84%** draw high traffic, against **60.6%** under
the current hand-picked process — so the 80% target is met. The model is a logistic regression
at a decision threshold of 0.61. That 84% rests on 121 recommendations from one test split, so
it carries a margin of error of about ±6.5 points: the claim is "at or above 80%", not "84.3%".

## Repo layout

```
README.md                                  this file
Practical Exam - Recipe Site Traffic.pdf   the brief from DataCamp, as supplied
data/
    recipe_site_traffic_2212.csv           947 recipes, 8 columns; never modified
analysis/
    Recipe_Site_Traffic_Analysis.ipynb     the analysis, executed — the graded report
    key_numbers.md                         every quotable figure, and its source cell
presentation/
    tables.md                              the three slide tables, ready to paste
    slides/
        Recipe_Site_Traffic.pptx           the deck — script is in the speaker notes
        Recipe_Site_Traffic.pdf            the same deck, flattened
    text/
        script.md                          what to say, verbatim, with timings
        script.pdf                         the same script, for reading from
        texte pour la présentation.docx    the script as a Word document
    figures/
        fig01…fig09_*.png                  the nine charts, exported from the notebook
        figures.md                         which figure belongs on which slide
```

## Reproducing the analysis

Launch the notebook from `analysis/`: its paths are relative to that folder, so it reads
`../data/recipe_site_traffic_2212.csv`. Run it top to bottom on a clean kernel — it writes
`analysis/key_numbers.md` itself, the single source of every figure quoted in the deck. Every
stochastic step is seeded with 42, so the numbers reproduce exactly. On DataLab the CSV sits
beside the workbook, so `DATA_PATH` in cell 0.1 loses its `../` prefix there.

## Key decisions

- **A blank `high_traffic` is the negative class, not missing data.** The data dictionary
  marks only high traffic, so no mark means the recipe was shown and traffic was not high.
- **The 52 recipes with no nutrition panel are kept, not dropped.** Gaps are filled with the
  median of the recipe's own category, learned on the training split only, and a flag records
  that the panel was missing — that missingness turns out to carry signal.
- **All 11 category levels are kept, though the brief documents 10.** The undocumented
  `Chicken Breast` behaves differently from `Chicken`; merging them would lose information.
- **Success is the share of recommendations that succeed, not accuracy.** With one slot a day
  and a pool of candidates, a false positive costs a day of traffic while a false negative
  costs almost nothing — another good recipe takes the slot.

## The open assumption

All 373 unlabelled recipes are assumed to have been featured on the homepage. If some were
never shown, a blank means "untested" rather than "unpopular", and the headline numbers above
need revisiting. This is the first thing to confirm with the product team.
