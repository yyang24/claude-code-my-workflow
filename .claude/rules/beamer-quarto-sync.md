---
paths:
  - "Slides/**/*.tex"
  - "Quarto/**/*.qmd"
---

# Beamer → Quarto Auto-Sync Rule (MANDATORY)

**Every edit to a Beamer `.tex` file MUST be immediately synced to the corresponding Quarto `.qmd` file — automatically, without the user asking.** This is non-negotiable.

## The Rule

When you modify a Beamer `.tex` file, you MUST also apply the equivalent change to the Quarto `.qmd` (if it exists) **in the same task**, before reporting completion. Do NOT wait to be asked. Do NOT just "flag the drift." Just do it.

## Lecture Mapping

<!-- Customize this table for your lectures -->
| Lecture | Beamer | Quarto |
|---------|--------|--------|
| 1 | `Slides/Lecture01_Intro_Problem.tex` | `Quarto/Lecture01_Intro_Problem.qmd` |
| 2 | `Slides/Lecture02_Product_Dev.tex` | `Quarto/Lecture02_Product_Dev.qmd` |
| 3 | `Slides/Lecture03_Concept_Test.tex` | `Quarto/Lecture03_Concept_Test.qmd` |
| 4 | `Slides/Lecture04_Exploratory_Design.tex` | `Quarto/Lecture04_Exploratory_Design.qmd` |
| 5 | `Slides/Lecture05_Descriptive_Scaling.tex` | `Quarto/Lecture05_Descriptive_Scaling.qmd` |
| 6 | `Slides/Lecture06_Questionnaire.tex` | `Quarto/Lecture06_Questionnaire.qmd` |
| 7 | `Slides/Lecture07_Hypothesis_ANOVA.tex` | `Quarto/Lecture07_Hypothesis_ANOVA.qmd` |
| 8 | `Slides/Lecture08_Regression_Sampling.tex` | `Quarto/Lecture08_Regression_Sampling.qmd` |
| 9 | `Slides/Lecture09_Fieldwork_Report.tex` | `Quarto/Lecture09_Fieldwork_Report.qmd` |
| 10 | `Slides/Lecture10_Experimentation_Market.tex` | `Quarto/Lecture10_Experimentation_Market.qmd` |
<!-- Add rows as you create lectures -->

## Workflow (Every Time)

1. Apply fix to Beamer `.tex`
2. **Immediately** apply equivalent fix to Quarto `.qmd`
3. Compile Beamer (3-pass xelatex)
4. Render Quarto (`./scripts/sync_to_docs.sh LectureN`)
5. Only then report task complete

## LaTeX → Quarto Translation Reference

| Beamer | Quarto Equivalent |
| ------ | ----------------- |
| `\textbf{text}` | `**text**` |
| `\textit{text}` | `*text*` |
| `\textcolor{red}{text}` | `[text]{style="color: red;"}` |
| `\textcolor{positive}{text}` | `[text]{.positive}` |
| `\textcolor{negative}{text}` | `[text]{.negative}` |
| `\item text` | `- text` |
| `\begin{block}{Title}` | `::: {.callout-note title="Title"}` |
| `\begin{alertblock}{Title}` | `::: {.callout-warning title="Title"}` |
| `\begin{exampleblock}{Title}` | `::: {.callout-tip title="Title"}` |
| `$formula$` | `$formula$` (same) |
| `\begin{columns}` | `:::: {.columns}` |
| `\begin{column}{0.5\textwidth}` | `::: {.column width="50%"}` |

## When NOT to Sync

- Quarto file doesn't exist yet
- Change is LaTeX-only infrastructure (preamble, theme files)
- Explicitly told to skip Quarto sync

## Enforcement

Before marking any Beamer editing task as complete, check:
> "Did I also update the Quarto file?"

If the answer is no and a Quarto file exists, **you are NOT done.**

## When to Update This Table

After creating a new Quarto translation, add it to the mapping table above.
