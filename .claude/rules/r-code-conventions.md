---
paths:
  - "**/*.R"
  - "Figures/**/*.R"
  - "scripts/**/*.R"
---

# R Code Standards

**Standard:** Senior Principal Data Engineer + PhD researcher quality

---

## 1. Reproducibility

- `set.seed()` called ONCE at top (YYYYMMDD format)
- All packages loaded at top via `library()` (not `require()`)
- All paths relative to repository root
- `dir.create(..., recursive = TRUE)` for output directories

## 2. Function Design

- `snake_case` naming, verb-noun pattern
- Roxygen-style documentation
- Default parameters, no magic numbers
- Named return values (lists or tibbles)

## 3. Domain Correctness

<!-- Customize for your field's known pitfalls -->
- Verify statistical test implementations match slide formulas
- Check known package bugs (document below in Common Pitfalls)
- Likert data: explicitly decide ordinal vs. interval treatment and document rationale
- Chi-square: verify expected frequency ≥ 5 before using `chisq.test()`; use `fisher.test()` otherwise
- ANOVA: check for balanced designs; use `car::Anova(..., type = "III")` for unbalanced
- Web scraping: always set `encoding = "UTF-8"` for Chinese content
- Sentiment analysis: use `jiebaR` for Chinese tokenization; separate languages before scoring

## 4. Visual Identity

```r
# --- CUHK institutional palette ---
cuhk_purple    <- "#6B2D8B"
cuhk_gold      <- "#EDAB56"
dark_gray      <- "#3D3D3D"
positive_green <- "#15803d"
negative_red   <- "#b91c1c"
```

### Custom Theme
```r
theme_cuhk <- function(base_size = 14) {
  theme_minimal(base_size = base_size) +
    theme(
      plot.title = element_text(face = "bold", color = cuhk_purple),
      legend.position = "bottom"
    )
}
```

### Figure Dimensions for Beamer
```r
ggsave(filepath, width = 12, height = 5, bg = "transparent")
```

## 5. RDS Data Pattern

**Heavy computations saved as RDS; slide rendering loads pre-computed data.**

```r
saveRDS(result, file.path(out_dir, "descriptive_name.rds"))
```

## 6. Common Pitfalls

<!-- Add your field-specific pitfalls here -->
| Pitfall | Impact | Prevention |
|---------|--------|------------|
| Missing `bg = "transparent"` | White boxes on slides | Always include in ggsave() |
| Hardcoded paths | Breaks on other machines | Use relative paths |
| `chisq.test()` with expected count < 5 | Invalid test results | Check with `chisq.test(x)$expected`; use `fisher.test()` |
| Likert as numeric without `factor()` | Wrong analysis | Use `factor(..., ordered = TRUE)` |
| `aov()` with unbalanced groups | Biased F-test | Use `car::Anova(..., type = "III")` |
| `read_html()` without encoding | Garbled Chinese text | Set `encoding = "UTF-8"` |
| `tidytext` for Chinese text | No/wrong tokens | Use `jiebaR` for segmentation |
| Mixed-language sentiment | Wrong scores | Separate languages first |

## 7. Line Length & Mathematical Exceptions

**Standard:** Keep lines <= 100 characters.

**Exception: Mathematical Formulas** -- lines may exceed 100 chars **if and only if:**

1. Breaking the line would harm readability of the math (influence functions, matrix ops, finite-difference approximations, formula implementations matching paper equations)
2. An inline comment explains the mathematical operation:
   ```r
   # Sieve projection: inner product of residuals onto basis functions P_k
   alpha_k <- sum(r_i * basis[, k]) / sum(basis[, k]^2)
   ```
3. The line is in a numerically intensive section (simulation loops, estimation routines, inference calculations)

**Quality Gate Impact:**
- Long lines in non-mathematical code: minor penalty (-1 to -2 per line)
- Long lines in documented mathematical sections: no penalty

## 8. Code Quality Checklist

```
[ ] Packages at top via library()
[ ] set.seed() once at top
[ ] All paths relative
[ ] Functions documented (Roxygen)
[ ] Figures: transparent bg, explicit dimensions
[ ] RDS: every computed object saved
[ ] Comments explain WHY not WHAT
```
