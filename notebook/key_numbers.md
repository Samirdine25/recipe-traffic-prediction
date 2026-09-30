# Key numbers — Recipe Site Traffic

Every figure below was produced by an executed cell of `analysis/Recipe_Site_Traffic_Analysis.ipynb`
and is named with the cell that produced it. **The presentation may quote these numbers and
no others.** If a figure is needed that is not here, compute it in the notebook first.

- Source data: `data/recipe_site_traffic_2212.csv` — 947 rows x 8 columns (unmodified)
- Random seed: 42 | split: stratified, test_size = 0.25 | CV: 5-fold stratified, shuffled
- Chosen model: Logistic regression (baseline) at a decision threshold of 0.61
- Success criterion: precision on the High class >= 80% — **MET** (84.3%)

## Dataset

| Figure | Value | Notebook cell |
|---|---|---|
| Rows in the raw dataset | 947 | 1.1 |
| Columns in the raw dataset | 8 | 1.1 |
| Fully duplicated rows | 0 | 1.1 |
| Rows with all four nutrition values missing | 52 | 1.3 |
| Share of rows with the nutrition panel missing | 5.5% | 1.3 |
| Category levels observed in the data | 11 | 1.4 |
| Category levels promised by the data dictionary | 10 | 1.4 |
| Undocumented category level found | Chicken Breast | 1.4 |
| Recipes in the undocumented category | 98 | 1.4 |
| Non-numeric servings labels | 4 as a snack; 6 as a snack | 1.5 |
| Rows with a text servings label | 3 | 1.5 |
| Rows after cleaning (none dropped) | 947 | 1.7 |

## Target

| Figure | Value | Notebook cell |
|---|---|---|
| High-traffic recipes in the data | 574 | 1.6 |
| Not-high-traffic recipes in the data | 373 | 1.6 |
| Base rate of high traffic (current human selection) | 60.6% | 1.6 |

## Exploration

| Figure | Value | Notebook cell |
|---|---|---|
| Median calories per recipe | 289 kcal | 2.1 |
| Smallest category size | 71 recipes | 2.2 |
| Strongest single nutrient rank-correlation with high traffic | 0.119 | 2.4 |
| High-traffic rate, servings spread (min-max) | 57.4% to 65.2% | 2.5 |
| Servings chi-square p-value | 0.434 | 2.5 |
| High-traffic rate when the nutrition panel is missing | 75.0% | 2.5 |
| High-traffic rate when the nutrition panel is present | 59.8% | 2.5 |

## Category rates

| Figure | Value | Notebook cell |
|---|---|---|
| High-traffic rate - Vegetable | 98.8% | 2.3 |
| High-traffic rate - Potato | 94.3% | 2.3 |
| High-traffic rate - Pork | 91.7% | 2.3 |
| High-traffic rate - Chicken Breast | 46.9% | 2.3 |
| High-traffic rate - Chicken | 36.5% | 2.3 |
| High-traffic rate - Breakfast | 31.1% | 2.3 |
| High-traffic rate - Beverages | 5.4% | 2.3 |
| Beverages - high-traffic recipes out of the category total | 5 of 92 | 2.3 |
| Vegetable - high-traffic recipes out of the category total | 82 of 83 | 2.3 |
| Spread in high-traffic rate across categories (pp) | 93 pp | 2.3 |
| Categories above the site-wide base rate | 7 of 11 | 2.3 |

## Modelling

| Figure | Value | Notebook cell |
|---|---|---|
| Training recipes | 710 | 3.1 |
| Test recipes | 237 | 3.1 |
| Base rate in the test set | 60.8% | 3.1 |
| High-traffic recipes in the test set | 144 | 3.1 |
| Logistic regression CV ROC-AUC (train) | 0.812 | 3.4 |
| Random forest CV ROC-AUC (train) | 0.804 | 3.4 |

## Model comparison

| Figure | Value | Notebook cell |
|---|---|---|
| Logistic regression - precision (High) at threshold 0.50 | 0.831 | 4.1 |
| Logistic regression - recall (High) at threshold 0.50 | 0.750 | 4.1 |
| Logistic regression - F1 (High) at threshold 0.50 | 0.788 | 4.1 |
| Logistic regression - accuracy at threshold 0.50 | 0.755 | 4.1 |
| Logistic regression - test ROC-AUC | 0.846 | 4.1 |
| Logistic regression - test average precision | 0.902 | 4.1 |
| Random forest - precision (High) at threshold 0.50 | 0.813 | 4.1 |
| Random forest - recall (High) at threshold 0.50 | 0.757 | 4.1 |
| Random forest - F1 (High) at threshold 0.50 | 0.784 | 4.1 |
| Random forest - accuracy at threshold 0.50 | 0.747 | 4.1 |
| Random forest - test ROC-AUC | 0.820 | 4.1 |
| Random forest - test average precision | 0.884 | 4.1 |

## Chosen operating point

| Figure | Value | Notebook cell |
|---|---|---|
| Chosen decision threshold | 0.61 | 4.3 |
| Out-of-fold precision at the chosen threshold | 0.801 | 4.3 |
| Out-of-fold recall at the chosen threshold | 0.758 | 4.3 |
| Out-of-fold precision at the default 0.50 threshold | 0.785 | 4.3 |
| Chosen model | Logistic regression (baseline) | 4.4 |
| Test precision at the chosen threshold | 0.843 | 4.4 |
| Test recall at the chosen threshold | 0.708 | 4.4 |
| Test F1 at the chosen threshold | 0.770 | 4.4 |
| Test accuracy at the chosen threshold | 0.743 | 4.4 |
| Recall given up versus the default threshold | 0.042 | 4.4 |
| Successful recommendations on the test set | 102 | 4.4 |
| Total recommendations on the test set | 121 | 4.4 |
| Unpopular recipes recommended on the test set (false positives) | 19 | 4.4 |
| High-traffic recipes passed over (false negatives) | 42 | 4.4 |
| Successful recommendations out of ten | 8.4 in 10 | 4.4 |
| Precision among the top 20 ranked test recipes | 100.0% | 4.5 |
| Precision among the top 50 ranked test recipes | 100.0% | 4.5 |

## Model explanation

| Figure | Value | Notebook cell |
|---|---|---|
| Vegetable odds ratio vs the average recipe | 9.7x | 4.6 |
| Beverages odds ratio vs the average recipe | 0.06x | 4.6 |
| Categories that raise the odds of high traffic (top three) | Vegetable, Potato, Pork | 4.6 |
| Categories that lower the odds of high traffic most | Beverages, Breakfast | 4.6 |

## Business metric

| Figure | Value | Notebook cell |
|---|---|---|
| Featured recipes needed for a +/-10pp margin of error | 51 | 5.1 |
| Featured recipes needed for a +/-7pp margin of error | 104 | 5.1 |
| Featured recipes needed for a +/-5pp margin of error | 204 | 5.1 |
| Margin of error on the initial model estimate | +/- 6.5% | 5.1 |
| Homepage hit rate - current process (initial value) | 60.6% | 5.1 |
| Homepage hit rate - model-assisted (initial value) | 84.3% | 5.1 |
| Homepage hit rate - lift in percentage points | +23.7 pp | 5.1 |
| Homepage hit rate - relative lift | +39.1% | 5.1 |
| Margin of error on a 4-week window | +/- 13.5% | 5.1 |
| Current process, out of ten featured recipes | 6.1 in 10 | 5.1 |

## Figures — exported to `presentation/figures/`, and where each one is used

| Figure | Cell | Export | Slide | What it shows |
|---|---|---|---|---|
| Figure 1 — Calories per recipe (histogram, log scale) | 2.1 | `fig01_calories_distribution.png` | — | Distribution shape; justifies keeping outliers |
| Figure 2 — Recipes per category (bar chart) | 2.2 | `fig02_recipes_per_category.png` | — | The 11 categories are evenly sized |
| Figure 3 — High-traffic rate by category | 2.3 | `fig03_high_traffic_by_category.png` | **4** | **The key chart**: 5% to 99% by category |
| Figure 4 — Nutrition by outcome (box plots, log scale) | 2.4 | `fig04_nutrition_by_outcome.png` | **5** | Nutrition barely separates the outcomes |
| Figure 5 — Servings and missing nutrition panel | 2.5 | `fig05_servings_and_missing_panel.png` | 5 (alt) | Servings flat; missing panel mildly positive |
| Figure 6 — Precision-recall curves, both models | 4.2 | `fig06_precision_recall_curves.png` | Q&A | Both clear the 80% line; logistic regression leads |
| Figure 7 — Precision and recall against threshold | 4.3 | `fig07_threshold_selection.png` | **backup** | The trade-off, and how the cut-off was chosen |
| Figure 8 — Confusion matrix at the chosen threshold | 4.4 | `fig08_test_set_outcomes.png` | **6** | 102 of 121 recommendations succeeded |
| Figure 9 — Odds ratios by category | 4.6 | `fig09_model_drivers.png` | Q&A | Why a recipe is predicted popular |

## Tables — rebuilt as pasteable markdown in `presentation/tables.md`

Printed cell output is not slide material; each table below is re-cut and re-headed in plain
English in `presentation/tables.md`, ready to paste as a native slide table.

| Table | Cell | Slide | Trimmed to |
|---|---|---|---|
| Data checks that failed | 1.8 | **3** | the 4 discrepancy rows, 3 plain-English columns |
| If we only featured the best-scoring recipes | 4.5 | **7** | top 20 / 50 / 100 — the primary visual on slide 7 |
| How long before the number means anything | 5.1 | **8** | 4 weeks / 90 days / 1 year |
| Model comparison | 4.1 | **excluded** | stays in the notebook: every column is a term this audience cannot be given |

## Wording for a non-technical audience

- "About 8 out of every 10 recipes we recommend do get high traffic, against about 6 out of 10 today."
- "102 of the 121 recipes the model recommended in testing were popular."
- "Vegetable recipes get high traffic 99% of the time. Beverages, 5% of the time."
- "We are turning down about 42 good recipes out of 144 to keep the homepage reliable — and they can be featured another day."
