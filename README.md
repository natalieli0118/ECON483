# Does Academic Paper Title Complexity Influence Citation Counts?

## Overview

This project investigates whether stylistic features of academic paper titles influence citation outcomes in economics.

Using two independently collected datasets (OpenAlex and Semantic Scholar), I estimate a series of Ordinary Least Squares (OLS) regression models to examine whether title length, word complexity, and punctuation usage affect log citation counts.

The results suggest that most title complexity measures have little to no impact on citation performance, while structural factors such as publication year and open-access status are much stronger predictors.

---

## Research Question

Do longer or more stylistically complex titles lead to higher (or lower) academic impact?

Specifically:

- Does title length affect citations?
- Does complex wording reduce visibility?
- Do colons or question marks influence citation performance?

---

## Data

### Dataset 1 – OpenAlex
- 231 economics papers (2015–2020)
- Variables:
  - Citation count
  - Publication year
  - Number of authors
  - Open-access status
  - Title characteristics

### Dataset 2 – Semantic Scholar
- ~800 economics papers
- Used for replication and robustness
- Open-access not included (no variation)

---

## Key Variables

### Dependent Variable

$$
\log(\text{citations} + 1)
$$

(Log transformation used due to right-skewed citation distribution.)

---

### Title Complexity Measures

- `title_length` (word count)
- `avg_word_length`
- `has_colon` (0/1)
- `has_question` (0/1)

---

### Controls

- `publication_year`
- `num_authors`
- `open_access_dummy` (OpenAlex only)

---

## Econometric Methodology

### Baseline Model

$$
\log(citations_i + 1) = \beta_0 + \beta_1 TitleLength_i + u_i
$$

---

### Full Specification

$$
\log(citations_i + 1)= \beta_0
+ \beta_1 TitleLength_i
+ \beta_2 AvgWordLength_i
+ \beta_3 Colon_i
+ \beta_4 Question_i
+ \beta_5 NumAuthors_i
+ \beta_6 Year_i
+ u_i
$$

---

### Nonlinear Test

$$
\log(citations_i + 1)= \beta_0
+ \beta_1 TitleLength_i
+ \beta_2 TitleLength_i^2
+ X_i'\gamma
+ u_i
$$

Two-sided t-tests conducted for all coefficients.

---

## Main Results

### 1. Title Length

- Slight negative coefficient
- Not statistically significant
- Explains <1% of variation in simple model

Interpretation: Longer titles do **not** meaningfully reduce citations.

---

### 2. Word Complexity & Colon Usage

- Small coefficients
- Statistically insignificant across datasets
- No meaningful effect

---

### 3. Question-Style Titles

- Not significant in OpenAlex sample
- Negative and statistically significant in larger Semantic Scholar sample
- Suggests question-style titles may receive fewer citations

---

### 4. Structural Factors Matter More

- Publication year: strong negative effect (newer papers have less exposure time)
- Open-access status: positive and statistically significant
- Full model R² ≈ 0.24 (OpenAlex)

---

## Robustness & Diagnostics

- Quadratic specification shows no nonlinear relationship
- Residual plots show no strong violations of OLS assumptions
- Q–Q plots indicate approximate normality
- Results replicated across two independent datasets

---

## Conclusion

Most stylistic aspects of title complexity do not meaningfully influence citation outcomes in economics.

Academic impact appears to be driven primarily by structural factors such as exposure time and accessibility, rather than by title length or wording choices.

One exception: question-style titles may be associated with fewer citations.

---

## Tools Used

- R
- tidyverse
- broom
- car (hypothesis testing)
- OLS regression
- Data cleaning & transformation

---

## Author

Natalie Li  
Economics & Applied Mathematical Sciences  
University of Washington
