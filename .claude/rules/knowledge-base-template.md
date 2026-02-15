---
paths:
  - "Slides/**/*.tex"
  - "Quarto/**/*.qmd"
  - "scripts/**/*.R"
---

# Course Knowledge Base: MKTG5012 Marketing Research

## Notation Registry

| Rule | Convention | Example | Anti-Pattern |
|------|-----------|---------|-------------|
| Null hypothesis | H₀ (subscript zero) | H₀: μ₁ = μ₂ | H0, Ho |
| Alternative hypothesis | H₁ or Hₐ | H₁: μ₁ ≠ μ₂ | Ha, H1 |
| Significance level | α (alpha) | α = 0.05 | a = 0.05 |
| Sample size | n (lowercase) | n = 200 | N for sample (N is population) |
| Population size | N (uppercase) | N = 10,000 | n for population |
| p-value | p (lowercase italic) | p < 0.01 | P-value, p-Value |
| Chi-square | χ² | χ²(3) = 12.4 | X², chi-sq |
| Coefficient of determination | R² | R² = 0.85 | r², r-squared |
| Correlation coefficient | r (lowercase italic) | r = 0.72 | R for bivariate |
| Mean | x̄ (x-bar) for sample, μ for population | x̄ = 4.2 | X-bar, xbar |
| Standard deviation | s (sample), σ (population) | s = 1.3 | SD, std |
| Regression coefficient | β (beta) | β₁ = 0.45 | b1 |
| F-statistic | F | F(2, 97) = 5.32 | f-value |
| t-statistic | t | t(99) = 2.45 | T-value |

## Symbol Reference

| Symbol | Meaning | Introduced |
|--------|---------|------------|
| H₀ / H₁ | Null / alternative hypothesis | Lecture 7 |
| α | Significance level (Type I error) | Lecture 7 |
| χ² | Chi-square test statistic | Lecture 6 (R lab), Lecture 7 |
| t | t-test statistic | Lecture 6 (R lab), Lecture 7 |
| F | F-statistic (ANOVA) | Lecture 7 |
| R² | Coefficient of determination | Lecture 8 |
| β | Regression coefficient | Lecture 8 |
| r | Pearson correlation coefficient | Lecture 8 |
| n | Sample size | Lecture 5 |
| p | p-value | Lecture 7 |

## Lecture Progression

| # | Title | Core Question | Key Notation | Key Method |
|---|-------|--------------|-------------|------------|
| 1 | Intro to Marketing Research; Problem Definition | How do we frame a marketing research problem? | -- | Problem definition framework, research approach |
| 2 | Product Development Fundamentals | How do firms develop new products? | -- | Stage-gate process, NPD frameworks |
| 3 | Product Concept Test; Research Design | How do we test product concepts and design research? | -- | Concept testing, research design types |
| 4 | Exploratory Research Design | When and how do we use secondary data and qualitative methods? | -- | Focus groups, depth interviews, syndicated data |
| 5 | Descriptive Research; Measurement & Scaling | How do we design surveys and measure constructs? | n | Survey design, Likert scales, semantic differential |
| 6 | Scaling Techniques; Questionnaire Design | How do we build valid measurement instruments? | χ², t, r | Comparative/noncomparative scales, questionnaire flow |
| 7 | Hypothesis Testing; Cross-Tabulation; ANOVA | How do we test hypotheses with categorical and continuous data? | H₀, H₁, α, χ², F, p | Chi-square test, t-test, one-way ANOVA |
| 8 | Correlation, Regression; Sampling | How do we model relationships and draw representative samples? | R², β, r, n | OLS regression, sampling design, sample size |
| 9 | Fieldwork; Data Preparation; Reporting | How do we collect, clean, and present data? | -- | Web scraping, sentiment analysis, word clouds |
| 10 | Experimentation; Market Size & Share | How do we establish causality and size markets? | -- | Experimental design, market sizing toolkit |

## Empirical Applications

| Application | Paper | Dataset | Lecture(s) | Purpose |
|------------|-------|---------|------------|---------|
| Product concept evaluation | Iansiti et al. (2016) | Company product data | 2 | Stage-gate NPD process |
| Consumer choice & no-choice | Dhar (1997) | Experimental data | 3 | Product concept testing |
| Choice architecture | Fernbach et al. (2013) | Consumer surveys | 3 | Research design motivation |
| Market sizing | Steenburgh & Avery (2010) | Market data | 10 | Market size and share analysis |
| Survey reliability | Birnbaum (1999) | Between-subjects design | 5-6 | Measurement and scaling |

## Design Principles

| Principle | Evidence | Lectures Applied |
|-----------|----------|-----------------|
| Motivation before formalism | Students engage more when they see the business problem first | All lectures |
| Real-world examples first | Concrete cases anchor abstract methods | 2, 3, 10 |
| Max 3 new statistical concepts per slide | Cognitive load research | 7, 8 |
| Show R output alongside interpretation | Bridges theory-practice gap | 6, 7, 8, 9 |
| Build from descriptive to inferential | Scaffolds statistical reasoning | 5 → 6 → 7 → 8 |

## Anti-Patterns (Don't Do This)

| Anti-Pattern | What Happened | Correction |
|-------------|---------------|-----------|
| Likert data treated as interval without discussion | Students confused about assumptions | Explicitly discuss ordinal vs. interval debate |
| Chi-square on small expected counts | Misleading test results | Check expected frequency ≥ 5 rule |
| Regression without checking assumptions | Invalid inference | Always show residual diagnostics |
| Web scraping without encoding handling | Garbled Chinese text | Specify UTF-8 encoding explicitly |

## R Code Pitfalls

| Bug | Impact | Fix |
|-----|--------|-----|
| `chisq.test()` with small expected counts | Warning or incorrect p-value | Check expected frequencies; use `fisher.test()` if needed |
| Likert columns as numeric without `factor()` | Wrong analysis type | Use `factor(..., ordered = TRUE)` for ordinal Likert |
| `aov()` with unbalanced groups | Misleading F-test | Use Type III sums of squares via `car::Anova()` |
| `rvest::read_html()` without encoding | Garbled Chinese characters | Use `read_html(..., encoding = "UTF-8")` |
| `tidytext` without Chinese tokenization | Empty or wrong tokens | Use `jiebaR` for Chinese text segmentation |
| `sentiment()` on mixed-language text | Incorrect sentiment scores | Separate languages before analysis |
