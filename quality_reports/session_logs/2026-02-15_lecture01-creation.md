# Session Log: 2026-02-15 — Lecture 1 Creation

**Status:** IN PROGRESS

## Objective

Create Beamer slides for MKTG5012 Lecture 1: Introduction to Marketing Research + Defining the Problem & Developing an Approach. Content grounded in Malhotra (2020) Ch.1-2, Lam (2023) Ch.1-2 + Appendix 4, and the MKTG5012 syllabus.

## Key Context

- This is a continuation session. Previous sessions completed workflow configuration (Phase 1) and commit/merge (Phase 2).
- The `/create-lecture Lecture 1` skill was invoked in the prior session, source materials were read, and a 6-act structure was approved.
- All content must be original and textbook-grounded (user explicitly challenged approximations).

## Changes Made

| File | Change | Reason |
|------|--------|--------|
| `Preambles/header.tex` | Created CUHK-themed Beamer preamble | CUHK colors, fonts (Helvetica Neue, Menlo, PingFang SC), custom commands, lstlisting style |
| `Slides/Lecture01_Intro_Problem.tex` | Created 42-page lecture (6 acts) | Full Lecture 1 content with 8 TikZ diagrams, R code listings |
| `Slides/Lecture01_Intro_Problem.pdf` | Compiled output | 0 errors, one negligible 0.33pt vbox overflow |
| `CLAUDE.md` | Updated project state table | Lecture 1 Beamer marked as complete |

## Decisions & Fixes

- TikZ `step` style name conflicts with built-in key → renamed to `stepbox`/`stp`
- `\texttimes` undefined → replaced with `$\times$`
- Added `colortbl` package for `\rowcolor` in schedule table
- Added `[fragile]` to frames containing lstlisting
- Fixed overfull boxes: table sizing (`\scriptsize`), code trimming, spacing adjustments
- Used `\source{}` for attribution instead of `\cite{}` (biblatex)

## Lecture 1 Structure

1. **Act 0:** Course logistics (title, instructor, overview, assessment, AI policy, schedule)
2. **Act 1:** What is Marketing? (AMA definition, exchange triangle, 5/6Cs, STP)
3. **Act 2:** What is Marketing Research? (Malhotra definition, classification tree, role of MR, exercise)
4. **Act 3:** MR Process (6-step process, problem definition, approach development, roadmap)
5. **Act 4:** Marketing Research or Not? (bus coin, shampoo promotion, chocolate bar breakeven)
6. **Act 5:** R Lab (installation, console, RStudio, arithmetic, variables)

## Open Questions

- No Quarto translation yet (per single-source-of-truth rule, Beamer is authoritative)
- Review agents not yet run on the completed slides
- Changes not yet committed
