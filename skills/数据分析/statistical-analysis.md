# 统计分析

> Category: 数据分析 | Difficulty: intermediate | Last updated: 2026

## When to Use

当用户需要进行统计分析、选择合适的统计检验方法、解读统计结果或在论文中正确报告统计结果时使用此技能。适用于实验数据分析、A/B 测试、假设检验、回归分析等场景。当用户提及统计分析、假设检验、p-value、t-test、ANOVA、回归分析、statistical test 或显著性检验时触发。

## Instructions for AI Assistant

### 基本原则

1. **先检查假设**：使用统计检验前必须验证其前提假设
2. **选对方法**：根据数据类型、分布和研究设计选择合适的检验
3. **报告完整**：包含检验统计量、自由度、p 值和效应量
4. **避免 p-hacking**：不要反复检验直到得到显著结果
5. **效应量 > p 值**：p 值只说明是否有差异，效应量说明差异有多大

### 统计检验选择流程

```
                    ┌─────────────────────┐
                    │  研究问题是什么？     │
                    └──────────┬──────────┘
                               │
              ┌────────────────┼────────────────┐
              ▼                ▼                ▼
        ┌──────────┐    ┌──────────┐    ┌──────────┐
        │ 比较差异  │    │ 关联关系  │    │ 预测建模  │
        └─────┬────┘    └─────┬────┘    └─────┬────┘
              │                │                │
    ┌─────────┼─────┐    ┌────┼────┐      ┌────┼────┐
    ▼         ▼     ▼    ▼    ▼    ▼      ▼    ▼    ▼
  两组     多组  配对  相关 回归 分类  线性  逻辑  机器
         　            　        　     回归  回归  学习
```

#### 两组比较

```markdown
## Two-Group Comparison Decision Tree

### 1. 数据类型？
├── 连续变量（如成绩、时间）
│   ├── 正态分布？（Shapiro-Wilk 检验）
│   │   ├── 是 → 独立样本 t-test / 配对 t-test
│   │   └── 否 → Mann-Whitney U / Wilcoxon signed-rank
│   └── 方差齐性？（Levene 检验）
│       ├── 是 → Student's t-test
│       └── 否 → Welch's t-test
└── 分类变量（如通过率、成功率）
    └── Chi-square test / Fisher's exact test
```

#### 多组比较

```markdown
## Multi-Group Comparison Decision Tree

### 独立组
├── 正态 + 方差齐性
│   └── One-way ANOVA → 事后检验 (Tukey HSD / Bonferroni)
├── 非正态
│   └── Kruskal-Wallis → 事后检验 (Dunn's test)
└── 分类变量
    └── Chi-square test → 事后比较 (pairwise)

### 重复测量
├── 正态
│   └── Repeated measures ANOVA → 事后检验
└── 非正态
    └── Friedman test → 事后检验 (Wilcoxon + Bonferroni)
```

### Python 代码模板

#### 基础统计检验

```python
import numpy as np
import pandas as pd
from scipy import stats
import warnings

def check_normality(data, alpha=0.05):
    """检查数据是否服从正态分布"""
    stat, p_value = stats.shapiro(data)
    is_normal = p_value > alpha
    print(f"Shapiro-Wilk test: W={stat:.4f}, p={p_value:.4f}")
    print(f"Normal distribution: {'Yes' if is_normal else 'No'}")
    return is_normal

def check_equal_variance(*groups, alpha=0.05):
    """检查多组数据的方差齐性"""
    stat, p_value = stats.levene(*groups)
    is_equal = p_value > alpha
    print(f"Levene's test: F={stat:.4f}, p={p_value:.4f}")
    print(f"Equal variance: {'Yes' if is_equal else 'No'}")
    return is_equal

def two_sample_ttest(group1, group2, paired=False, alpha=0.05):
    """两组比较：t-test 或非参数检验"""
    # 正态性检验
    norm1 = check_normality(group1, alpha)
    norm2 = check_normality(group2, alpha)

    if norm1 and norm2:
        # 方差齐性检验
        eq_var = check_equal_variance(group1, group2, alpha)
        if paired:
            stat, p_value = stats.ttest_rel(group1, group2)
            test_name = "Paired t-test"
        else:
            if eq_var:
                stat, p_value = stats.ttest_ind(group1, group2, equal_var=True)
                test_name = "Student's t-test"
            else:
                stat, p_value = stats.ttest_ind(group1, group2, equal_var=False)
                test_name = "Welch's t-test"
    else:
        if paired:
            stat, p_value = stats.wilcoxon(group1, group2)
            test_name = "Wilcoxon signed-rank test"
        else:
            stat, p_value = stats.mannwhitneyu(group1, group2, alternative='two-sided')
            test_name = "Mann-Whitney U test"

    # 效应量
    if 't-test' in test_name:
        cohens_d = compute_cohens_d(group1, group2, paired)
        effect_report = f"Cohen's d = {cohens_d:.3f}"
    else:
        n1, n2 = len(group1), len(group2)
        rank_biserial = 1 - (2 * stat) / (n1 * n2)
        effect_report = f"Rank-biserial r = {abs(rank_biserial):.3f}"

    print(f"\n{'='*50}")
    print(f"Test: {test_name}")
    print(f"Statistic: {stat:.4f}")
    print(f"p-value: {p_value:.6f}")
    print(f"Effect size: {effect_report}")
    print(f"Significant at α={alpha}: {'Yes' if p_value < alpha else 'No'}")
    print(f"{'='*50}")

    return stat, p_value

def compute_cohens_d(group1, group2, paired=False):
    """计算 Cohen's d 效应量"""
    if paired:
        diff = np.array(group1) - np.array(group2)
        d = np.mean(diff) / np.std(diff, ddof=1)
    else:
        n1, n2 = len(group1), len(group2)
        var1, var2 = np.var(group1, ddof=1), np.var(group2, ddof=1)
        pooled_std = np.sqrt(((n1-1)*var1 + (n2-1)*var2) / (n1+n2-2))
        d = (np.mean(group1) - np.mean(group2)) / pooled_std
    return d

def one_way_anova(*groups, alpha=0.05):
    """多组比较：ANOVA 或非参数检验"""
    all_normal = all(check_normality(g, alpha) for g in groups)

    if all_normal:
        eq_var = check_equal_variance(*groups, alpha)
        if eq_var:
            stat, p_value = stats.f_oneway(*groups)
            test_name = "One-way ANOVA"
            # 效应量 eta-squared
            all_data = np.concatenate(groups)
            grand_mean = np.mean(all_data)
            ss_between = sum(len(g) * (np.mean(g) - grand_mean)**2 for g in groups)
            ss_total = np.sum((all_data - grand_mean)**2)
            eta_sq = ss_between / ss_total
            effect_report = f"η² = {eta_sq:.3f}"
        else:
            stat, p_value = stats.f_oneway(*groups)  # Welch's ANOVA
            test_name = "Welch's ANOVA"
            effect_report = "(use robust methods)"
    else:
        stat, p_value = stats.kruskal(*groups)
        test_name = "Kruskal-Wallis H test"
        # 效应量 epsilon-squared
        n_total = sum(len(g) for g in groups)
        epsilon_sq = (stat - len(groups) + 1) / (n_total - len(groups))
        effect_report = f"ε² = {epsilon_sq:.3f}"

    print(f"\n{'='*50}")
    print(f"Test: {test_name}")
    print(f"Statistic: {stat:.4f}")
    print(f"p-value: {p_value:.6f}")
    print(f"Effect size: {effect_report}")
    print(f"{'='*50}")

    # 事后检验
    if p_value < alpha:
        from itertools import combinations
        print("\nPost-hoc pairwise comparisons (Bonferroni corrected):")
        n_comparisons = len(list(combinations(range(len(groups)), 2)))
        for i, j in combinations(range(len(groups)), 2):
            _, p = stats.mannwhitneyu(groups[i], groups[j], alternative='two-sided')
            p_corrected = min(p * n_comparisons, 1.0)
            sig = "*" if p_corrected < alpha else ""
            print(f"  Group {i} vs Group {j}: p={p_corrected:.6f} {sig}")

    return stat, p_value

def chi_square_test(contingency_table):
    """卡方检验"""
    chi2, p_value, dof, expected = stats.chi2_contingency(contingency_table)

    # 效应量 Cramér's V
    n = np.sum(contingency_table)
    min_dim = min(contingency_table.shape) - 1
    cramers_v = np.sqrt(chi2 / (n * min_dim))

    print(f"Chi-square test: χ²={chi2:.4f}, df={dof}, p={p_value:.6f}")
    print(f"Cramér's V = {cramers_v:.3f}")

    # 检查期望频数
    if np.any(expected < 5):
        warnings.warn("Warning: Expected frequencies < 5 detected. "
                      "Consider Fisher's exact test.")
    return chi2, p_value, cramers_v

def correlation_analysis(x, y, method='auto', alpha=0.05):
    """相关分析"""
    if method == 'auto':
        norm_x = check_normality(x, alpha)
        norm_y = check_normality(y, alpha)
        method = 'pearson' if (norm_x and norm_y) else 'spearman'

    if method == 'pearson':
        stat, p_value = stats.pearsonr(x, y)
        test_name = "Pearson's r"
    elif method == 'spearman':
        stat, p_value = stats.spearmanr(x, y)
        test_name = "Spearman's ρ"
    else:
        stat, p_value = stats.kendalltau(x, y)
        test_name = "Kendall's τ"

    print(f"\nCorrelation: {test_name} = {stat:.4f}, p = {p_value:.6f}")
    return stat, p_value
```

#### 效应量解读

```python
def interpret_cohens_d(d):
    """解读 Cohen's d"""
    d = abs(d)
    if d < 0.2:
        return "negligible (< 0.2)"
    elif d < 0.5:
        return "small (0.2 - 0.5)"
    elif d < 0.8:
        return "medium (0.5 - 0.8)"
    else:
        return "large (> 0.8)"

def interpret_r(r):
    """解读相关系数"""
    r = abs(r)
    if r < 0.1:
        return "negligible (< 0.1)"
    elif r < 0.3:
        return "small (0.1 - 0.3)"
    elif r < 0.5:
        return "medium (0.3 - 0.5)"
    else:
        return "large (> 0.5)"

# 效应量标准速查表
EFFECT_SIZE_TABLE = """
┌──────────────────────┬──────────┬──────────┬──────────┐
│ Effect Size Measure  │  Small   │  Medium  │  Large   │
├──────────────────────┼──────────┼──────────┼──────────┤
│ Cohen's d            │   0.2    │   0.5    │   0.8    │
│ Pearson's r          │   0.1    │   0.3    │   0.5    │
│ η² (eta-squared)     │   0.01   │   0.06   │   0.14   │
│ Cohen's f            │   0.10   │   0.25   │   0.40   │
│ Cramér's V (2×2)     │   0.10   │   0.30   │   0.50   │
│ Odds Ratio           │  1.5     │   2.5    │   4.3    │
└──────────────────────┴──────────┴──────────┴──────────┘
"""
```

### R 代码模板

```r
# 基础设置
library(tidyverse)
library(effsize)      # 效应量
library(car)          # Levene检验
library(rstatix)      # 整洁的统计检验
library(ggpubr)       # 带统计标注的图

# 正态性检验
check_normality <- function(data, variable, group = NULL) {
  if (is.null(group)) {
    shapiro.test(data[[variable]])
  } else {
    data %>%
      group_by(!!sym(group)) %>%
      shapiro_test(!!sym(variable))
  }
}

# 两组 t-test
two_group_test <- function(data, value_var, group_var, paired = FALSE) {
  formula <- as.formula(paste(value_var, "~", group_var))

  if (paired) {
    result <- t.test(formula, data = data, paired = TRUE)
    effect <- cohen.d(data[[value_var]] ~ factor(data[[group_var]]), paired = TRUE)
  } else {
    result <- t.test(formula, data = data, paired = FALSE)
    effect <- cohen.d(data[[value_var]] ~ factor(data[[group_var]]))
  }

  cat("Test:", result$method, "\n")
  cat("t =", result$statistic, ", df =", result$parameter, "\n")
  cat("p-value =", result$p.value, "\n")
  cat("Cohen's d =", effect$estimate, "(", effect$magnitude, ")\n")
  cat("95% CI: [", result$conf.int[1], ",", result$conf.int[2], "]\n")
}

# One-way ANOVA with post-hoc
run_anova <- function(data, value_var, group_var) {
  formula <- as.formula(paste(value_var, "~", group_var))

  # ANOVA
  anova_result <- aov(formula, data = data)
  print(summary(anova_result))

  # 效应量
  library(effectsize)
  eta_sq <- eta_squared(anova_result)
  cat("\nEffect size (η²):", eta_sq$Eta2, "\n")

  # 事后检验 (Tukey HSD)
  posthoc <- TukeyHSD(anova_result)
  print(posthoc)

  # 或者使用 rstatix 整洁输出
  posthoc_tidy <- data %>%
    tukey_hsd(formula)
  print(posthoc_tidy)
}
```

### APA 统计报告格式

#### 基本格式规范

```markdown
## APA 7th Edition 统计报告规范

### t-test
格式: t(df) = X.XX, p = .XXX, d = X.XX
示例: t(58) = 3.45, p = .001, d = 0.89
说明: df 为整数，其他保留两位小数；p < .001 不写 p = .000

### ANOVA
格式: F(df_between, df_within) = X.XX, p = .XXX, η² = X.XX
示例: F(2, 87) = 5.23, p = .007, η² = .11

### Chi-square
格式: χ²(df, N = XXX) = X.XX, p = .XXX, V = X.XX
示例: χ²(2, N = 150) = 12.34, p = .002, V = .29

### Correlation
格式: r(df) = X.XX, p = .XXX
示例: r(98) = .45, p < .001

### Regression
格式: β = X.XX, SE = X.XX, t = X.XX, p = .XXX
示例: β = 0.35, SE = 0.08, t = 4.38, p < .001

### 非参数检验
Mann-Whitney: U = X.XX, p = .XXX, r = X.XX
Wilcoxon:     W = X.XX, p = .XXX, r = X.XX
Kruskal-Wallis: H(df) = X.XX, p = .XXX
Friedman:     χ²(df) = X.XX, p = .XXX
```

#### 论文结果部分模板

```markdown
## Results Section Template

### 描述统计
"The experimental group (M = 85.3, SD = 12.4) scored significantly
higher than the control group (M = 72.1, SD = 14.6)."

### 推断统计
"An independent-samples t-test revealed a statistically significant
difference between the experimental and control groups, t(58) = 3.45,
p = .001, d = 0.89, indicating a large effect size."

### ANOVA 结果
"A one-way ANOVA was conducted to compare the effect of learning
method (A, B, C) on test scores. There was a statistically significant
difference between groups, F(2, 87) = 5.23, p = .007, η² = .11.
Post-hoc comparisons using Tukey's HSD test indicated that Method A
(M = 88.2, SD = 9.1) was significantly higher than Method C
(M = 76.5, SD = 11.3, p = .003), but not significantly different
from Method B (M = 84.7, SD = 10.2, p = .241)."

### 相关分析
"A Pearson's correlation coefficient was computed to assess the
relationship between study hours and exam scores. There was a
moderate positive correlation, r(98) = .45, p < .001, indicating
that more study hours were associated with higher exam scores."

### 效应量报告
所有检验必须报告效应量及其置信区间。
"Mean difference = 13.2, 95% CI [5.8, 20.6], Cohen's d = 0.89."
```

### 统计功效分析

```python
from statsmodels.stats.power import (
    TTestIndPower, TTestPower, FTestAnovaPower,
    GofChisquarePower, NormalIndPower
)

def sample_size_estimation(effect_size, alpha=0.05, power=0.80, test_type='t'):
    """估算所需样本量"""
    if test_type == 't':
        analysis = TTestIndPower()
        n = analysis.solve_power(
            effect_size=effect_size,
            alpha=alpha,
            power=power,
            ratio=1.0,
            alternative='two-sided'
        )
    elif test_type == 'anova':
        analysis = FTestAnovaPower()
        n = analysis.solve_power(
            effect_size=effect_size,
            alpha=alpha,
            power=power,
            k_groups=3
        )

    print(f"Required sample size per group: {int(np.ceil(n))}")
    return int(np.ceil(n))

# 示例：检测中等效应量 (d=0.5) 需要的样本量
# α=0.05, power=0.80
sample_size_estimation(0.5, test_type='t')  # ≈ 64 per group
```

### 多重比较校正

```python
from statsmodels.stats.multitest import multipletests

def correct_multiple_comparisons(p_values, method='bonferroni'):
    """
    多重比较校正方法
    method: 'bonferroni', 'holm', 'fdr_bh' (Benjamini-Hochberg)
    """
    reject, p_corrected, _, _ = multipletests(
        p_values, alpha=0.05, method=method
    )

    print(f"Correction method: {method}")
    for i, (p_orig, p_corr, rej) in enumerate(zip(p_values, p_corrected, reject)):
        print(f"  Test {i+1}: p={p_orig:.4f} → corrected p={p_corr:.4f} "
              f"{'*' if rej else ''}")

    return p_corrected, reject

# 校正方法选择指南
"""
Bonferroni: 最保守，适合比较次数少 (<5) 的情况
Holm:       比 Bonferroni 更有检验力，推荐默认使用
FDR (BH):   控制错误发现率，适合探索性分析（多次比较）
"""
```

## Templates

### 两组比较快速分析模板

```python
# 快速执行两组比较的完整流程
import numpy as np
from scipy import stats

def quick_two_group(group1, group2, names=("Group A", "Group B")):
    """一步完成正态性检验→选择检验→计算效应量"""
    # 正态性
    _, p1 = stats.shapiro(group1)
    _, p2 = stats.shapiro(group2)
    if p1 > 0.05 and p2 > 0.05:
        stat, p = stats.ttest_ind(group1, group2)
        test = "t-test"
    else:
        stat, p = stats.mannwhitneyu(group1, group2)
        test = "Mann-Whitney U"
    print(f"{names[0]}: M={np.mean(group1):.2f}, SD={np.std(group1):.2f}")
    print(f"{names[1]}: M={np.mean(group2):.2f}, SD={np.std(group2):.2f}")
    print(f"Test: {test}, stat={stat:.4f}, p={p:.4f}")
```

### APA 结果报告模板

```
An independent-samples t-test revealed a statistically significant
difference between [Group A] (M = X.XX, SD = X.XX) and [Group B]
(M = X.XX, SD = X.XX), t(df) = X.XX, p = .XXX, d = X.XX.
```

### 样本量估算模板

```python
from statsmodels.stats.power import TTestIndPower
analysis = TTestIndPower()
n = analysis.solve_power(effect_size=0.5, alpha=0.05, power=0.80)
print(f"Required per group: {int(np.ceil(n))}")  # ≈ 64
```

## Common Patterns

### 分析流程标准化

```
1. 数据探索 → 描述统计、分布可视化
2. 假设检验预评估 → 正态性、方差齐性
3. 选择检验方法 → 参照决策树
4. 执行检验 → 同时计算效应量
5. 多重比较校正 → 如有必要
6. 结果报告 → 按 APA 格式
7. 可视化 → 带统计标注的图表
```

### 样本量与检验力

```markdown
| 效应量 (Cohen's d) | α=0.05, Power=0.80 | α=0.05, Power=0.90 |
|--------------------|--------------------|--------------------|
| 0.2 (小)           | 394/组             | 526/组             |
| 0.5 (中)           | 64/组              | 85/组              |
| 0.8 (大)           | 26/组              | 34/组              |
```

## Pitfalls to Avoid

1. **不检查假设就用参数检验**：必须先做正态性和方差齐性检验
2. **p = 0.000 的写法**：应写为 p < .001
3. **只报告 p 值不报告效应量**：p 值受样本量影响，效应量更有意义
4. **p-hacking**：不要尝试多种检验直到得到显著结果
5. **相关 ≠ 因果**：相关分析不能推断因果关系
6. **样本量过小**：小样本的统计检验力不足，容易产生假阴性
7. **忽略多重比较**：多次检验需要校正，否则假阳性率膨胀
8. **对非正态数据用均值和标准差**：非正态数据应报告中位数和四分位距
9. **自动选择最显著的结果报告**：应预先注册分析计划
10. **忽略缺失数据处理**：明确说明缺失数据的处理方式

## Resources

- [statsmodels Documentation](https://www.statsmodels.org/)
- [scipy.stats Documentation](https://docs.scipy.org/doc/scipy/reference/stats.html)
- [R statistical computing](https://www.r-project.org/)
- [G*Power - 统计功效分析软件](https://www.psychologie.hhu.de/gpower)
- [APA 7th Edition Publication Manual](https://apastyle.apa.org/products/publication-manual-7th-edition)
- [Effect Size Calculator](https://www.socscistatistics.com/effectsize/)
