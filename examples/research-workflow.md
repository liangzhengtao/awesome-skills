# 🔬 Example: Complete Research Workflow

**[English](#english) | [中文](#中文)**

This example demonstrates how to combine multiple skills for a complete research workflow, from literature review to paper submission.

<a name="english"></a>

## 🇬🇧 English

### Scenario

You're a PhD student working on a new attention mechanism for Transformers. You need to:

1. Review existing literature on attention mechanisms
2. Design and run experiments
3. Analyze results with proper statistics
4. Create publication-quality figures
5. Write the paper
6. Submit to a conference

Here's how skills help at each step.

---

### Step 1: Literature Review 🔍

**Skill:** `literature-review`

```bash
cp skills/literature-review.md CLAUDE.md
```

**Prompt:**
```
Help me do a literature review on efficient attention mechanisms for Transformers.
Focus on:
1. Linear attention variants (2020-2024)
2. Sparse attention patterns
3. Multi-query and grouped-query attention
4. Flash Attention and hardware-aware methods

For each paper, extract:
- Key contribution
- Complexity analysis
- Benchmark results
- Limitations

Organize by approach category and create a comparison table.
```

**Output:** A structured literature review with 30+ papers organized by approach, including a comparison table and identified research gaps.

---

### Step 2: Experiment Design & ML Tracking 🧪

**Skill:** `ml-experiment`

```bash
cat skills/literature-review.md skills/ml-experiment.md > CLAUDE.md
```

**Prompt:**
```
Design experiments for my new "Hierarchical Sparse Attention" mechanism.

Baselines to compare:
- Standard Multi-Head Attention
- Flash Attention 2
- Linear Attention (Performer)
- Sparse Attention (BigBird)

Datasets:
- Language modeling: OpenWebText
- Long document: SCROLLS
- Summarization: CNN/DailyMail

Metrics:
- Perplexity
- Throughput (tokens/sec)
- Memory usage
- FLOPs

Set up the experiment code with proper:
- Random seeds for reproducibility
- Learning rate scheduling
- Early stopping
- Wandb logging
```

**Output:** Complete experiment code with proper baselines, reproducibility settings, and experiment tracking.

---

### Step 3: Data Analysis 📊

**Skill:** `statistical-analysis`

```bash
cp skills/statistical-analysis.md .cursorrules
```

**Prompt:**
```
Analyze the experiment results in results.csv.

Columns: model, dataset, perplexity, throughput, memory, flops, run_id

I need:
1. Descriptive statistics for each model across all datasets
2. Check normality of the data (Shapiro-Wilk)
3. Compare my model (hierarchical_sparse) vs each baseline:
   - If normal: paired t-test with Cohen's d
   - If not normal: Wilcoxon signed-rank with rank-biserial correlation
4. 95% confidence intervals for all differences
5. Bonferroni correction for multiple comparisons
6. Create a summary table in APA format

Generate the statistical report section for the paper.
```

**Output:** Complete statistical analysis with:
- Normality test results
- Appropriate statistical tests selected automatically
- Effect sizes and confidence intervals
- APA-formatted results section ready for the paper

---

### Step 4: Data Visualization 📈

**Skill:** `data-visualization`

```bash
cat skills/statistical-analysis.md skills/data-visualization.md > CLAUDE.md
```

**Prompt:**
```
Create publication-quality figures for my paper. Use Nature journal style.

Figure 1: Bar chart comparing perplexity across models and datasets
- Grouped bars with error bars (95% CI)
- Significance markers (* p<0.05, ** p<0.01, *** p<0.001)
- Color palette: colorblind-friendly

Figure 2: Line plot showing throughput vs sequence length
- Multiple lines for each model
- Shaded regions for std dev
- Log scale on x-axis

Figure 3: Scatter plot of perplexity vs memory usage
- Different markers for each model
- Annotate my model's point
- Add Pareto frontier

Figure 4: Heatmap of ablation study results
- Rows: components removed
- Columns: metrics
- Diverging colormap

Save all figures as:
- PDF (for paper)
- PNG 300dpi (for review)
- SVG (for editing)
```

**Output:** Four publication-ready figures with consistent styling, proper labels, and multiple output formats.

---

### Step 5: Paper Writing ✍️

**Skill:** `latex-paper`

```bash
cat skills/latex-paper.md skills/data-visualization.md skills/academic-english.md > CLAUDE.md
```

**Prompt:**
```
Write a LaTeX paper for NeurIPS 2025.

Title: "Hierarchical Sparse Attention: Linear Complexity with Sub-quadratic Quality"

Structure:
1. Abstract (150 words)
2. Introduction (1.5 pages)
   - Motivation: quadratic attention is the bottleneck
   - Gap: existing methods sacrifice too much quality
   - Our approach: hierarchical sparsity pattern
   - Results: 95% of full attention quality at 3x speed
3. Related Work (1 page)
   - Use the literature review from Step 1
4. Method (2 pages)
   - Mathematical formulation
   - Algorithm pseudocode
   - Complexity analysis
5. Experiments (2 pages)
   - Setup description
   - Main results (reference Figures 1-3)
   - Ablation study (reference Figure 4)
6. Conclusion (0.5 pages)

Requirements:
- NeurIPS 2025 LaTeX template
- Use \label and \ref for all figures and tables
- BibTeX for references
- Proper mathematical notation
- No filler phrases, concise writing

Here are the experimental results and figures to reference:
[paste statistical results from Step 3]
```

**Output:** Complete NeurIPS-formatted LaTeX paper with:
- Proper template and formatting
- All figures correctly referenced
- Statistical results reported correctly
- BibTeX bibliography
- Compiles without errors

---

### Step 6: Conference Submission 📬

**Skill:** `conference-submission`

```bash
cat skills/latex-paper.md skills/conference-submission.md > CLAUDE.md
```

**Prompt:**
```
Prepare my paper for NeurIPS 2025 submission.

Check:
1. Page limit (9 pages excluding references)
2. Anonymous review requirements (no author info)
3. Supplementary material organization
4. Checklist items from the call for papers
5. PDF compilation without errors
6. File size limits
7. Blind review compliance

Generate:
1. Final compiled PDF
2. Supplementary material archive
3. Author response template
4. Submission checklist
```

**Output:** Submission-ready package with checklist verification.

---

### Complete Workflow Summary

```
┌─────────────────────────────────────────────────────────────┐
│                    Research Workflow                         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  1. literature-review ──────► Structured lit review         │
│         │                                                   │
│         ▼                                                   │
│  2. ml-experiment ──────────► Experiment code + tracking    │
│         │                                                   │
│         ▼                                                   │
│  3. statistical-analysis ───► Proper stats + APA report     │
│         │                                                   │
│         ▼                                                   │
│  4. data-visualization ─────► Publication-quality figures   │
│         │                                                   │
│         ▼                                                   │
│  5. latex-paper ────────────► Complete paper in LaTeX       │
│         │                                                   │
│         ▼                                                   │
│  6. conference-submission ──► Submission-ready package      │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Tips for Combining Skills

1. **Concatenate related skills** for complex tasks:
   ```bash
   cat skills/latex-paper.md skills/academic-english.md > CLAUDE.md
   ```

2. **Switch skills** as you move between phases:
   ```bash
   # During analysis phase
   cp skills/statistical-analysis.md CLAUDE.md

   # During writing phase
   cp skills/latex-paper.md CLAUDE.md
   ```

3. **Layer skills** for comprehensive instructions:
   ```bash
   # Base + specific
   cat skills/latex-paper.md skills/conference-submission.md > CLAUDE.md
   ```

4. **Keep a master file** with all your customized skills:
   ```bash
   cat skills/*.md > .cursorrules
   ```

---

<a name="中文"></a>

## 🇨🇳 中文

### 场景

你是一名博士生，正在研究一种新的 Transformer 注意力机制。你需要：

1. 综述注意力机制相关文献
2. 设计并运行实验
3. 用正确的统计方法分析结果
4. 创建出版质量的图表
5. 撰写论文
6. 投稿会议

以下是每个步骤如何使用技能。

---

### 第一步：文献综述 🔍

**技能：** `literature-review`

```bash
cp skills/literature-review.md CLAUDE.md
```

**提示词：**
```
帮我做一个关于 Transformer 高效注意力机制的文献综述。
重点关注：
1. 线性注意力变体（2020-2024）
2. 稀疏注意力模式
3. 多查询和分组查询注意力
4. Flash Attention 和硬件感知方法

对每篇论文，提取：
- 核心贡献
- 复杂度分析
- 基准测试结果
- 局限性

按方法类别组织，并创建对比表格。
```

**产出：** 结构化的文献综述，包含 30+ 篇论文按方法分类，包括对比表格和研究空白。

---

### 第二步：实验设计与 ML 追踪 🧪

**技能：** `ml-experiment`

```bash
cat skills/literature-review.md skills/ml-experiment.md > CLAUDE.md
```

**提示词：**
```
为我的"分层稀疏注意力"机制设计实验。

对比基线：
- 标准多头注意力
- Flash Attention 2
- 线性注意力（Performer）
- 稀疏注意力（BigBird）

数据集：
- 语言建模：OpenWebText
- 长文档：SCROLLS
- 摘要生成：CNN/DailyMail

指标：
- 困惑度
- 吞吐量（tokens/sec）
- 内存使用
- FLOPs

设置实验代码，包含：
- 随机种子以确保可复现性
- 学习率调度
- 早停
- Wandb 日志记录
```

**产出：** 完整的实验代码，包含正确的基线、可复现性设置和实验追踪。

---

### 第三步：数据分析 📊

**技能：** `statistical-analysis`

```bash
cp skills/statistical-analysis.md .cursorrules
```

**提示词：**
```
分析 results.csv 中的实验结果。

列：model, dataset, perplexity, throughput, memory, flops, run_id

我需要：
1. 每个模型在所有数据集上的描述性统计
2. 检查数据的正态性（Shapiro-Wilk）
3. 将我的模型（hierarchical_sparse）与每个基线对比：
   - 如果正态：配对 t 检验 + Cohen's d
   - 如果非正态：Wilcoxon 符号秩检验 + 秩二列相关
4. 所有差异的 95% 置信区间
5. 多重比较的 Bonferroni 校正
6. 创建 APA 格式的汇总表

生成论文的统计分析部分。
```

**产出：** 完整的统计分析，包括：
- 正态性检验结果
- 自动选择合适的统计检验
- 效应量和置信区间
- APA 格式的结果部分

---

### 第四步：数据可视化 📈

**技能：** `data-visualization`

```bash
cat skills/statistical-analysis.md skills/data-visualization.md > CLAUDE.md
```

**提示词：**
```
为我的论文创建出版质量的图表。使用 Nature 期刊风格。

图 1：柱状图比较各模型在数据集上的困惑度
- 分组柱状图 + 误差线（95% CI）
- 显著性标记（* p<0.05, ** p<0.01, *** p<0.001）
- 配色：色盲友好

图 2：折线图展示吞吐量 vs 序列长度
- 每个模型一条线
- 标准差阴影区域
- x 轴对数刻度

图 3：散点图展示困惑度 vs 内存使用
- 不同模型用不同标记
- 标注我的模型的点
- 添加 Pareto 前沿

图 4：消融实验结果热力图
- 行：移除的组件
- 列：指标
- 发散色图

所有图表保存为：
- PDF（用于论文）
- PNG 300dpi（用于审稿）
- SVG（用于编辑）
```

**产出：** 四张出版就绪的图表，具有一致的样式、正确的标签和多种输出格式。

---

### 第五步：论文撰写 ✍️

**技能：** `latex-paper`

```bash
cat skills/latex-paper.md skills/data-visualization.md skills/academic-english.md > CLAUDE.md
```

**提示词：**
```
为 NeurIPS 2025 写一篇 LaTeX 论文。

标题："Hierarchical Sparse Attention: Linear Complexity with Sub-quadratic Quality"

结构：
1. 摘要（150 词）
2. 引言（1.5 页）
   - 动机：二次注意力是瓶颈
   - 空白：现有方法牺牲太多质量
   - 我们的方法：分层稀疏模式
   - 结果：95% 全注意力质量，3 倍速度
3. 相关工作（1 页）
   - 使用第一步的文献综述
4. 方法（2 页）
   - 数学公式化
   - 算法伪代码
   - 复杂度分析
5. 实验（2 页）
   - 设置描述
   - 主要结果（引用图 1-3）
   - 消融研究（引用图 4）
6. 结论（0.5 页）

要求：
- NeurIPS 2025 LaTeX 模板
- 所有图表使用 \label 和 \ref
- BibTeX 引用
- 正确的数学符号
- 简洁写作，无填充短语

以下是实验结果和图表：
[粘贴第三步的统计结果]
```

**产出：** 完整的 NeurIPS 格式 LaTeX 论文，包括：
- 正确的模板和格式
- 所有图表正确引用
- 统计结果正确报告
- BibTeX 参考文献
- 编译无错误

---

### 第六步：会议投稿 📬

**技能：** `conference-submission`

```bash
cat skills/latex-paper.md skills/conference-submission.md > CLAUDE.md
```

**提示词：**
```
为 NeurIPS 2025 投稿准备我的论文。

检查：
1. 页数限制（不含参考文献 9 页）
2. 匿名审稿要求（无作者信息）
3. 补充材料组织
4. 征稿通知中的检查清单
5. PDF 编译无错误
6. 文件大小限制
7. 盲审合规性

生成：
1. 最终编译 PDF
2. 补充材料压缩包
3. 作者回复模板
4. 投稿检查清单
```

**产出：** 投稿就绪的文件包，附检查清单验证。

---

### 完整工作流总结

```
┌─────────────────────────────────────────────────────────────┐
│                    研究工作流                                 │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  1. literature-review ──────► 结构化文献综述                  │
│         │                                                   │
│         ▼                                                   │
│  2. ml-experiment ──────────► 实验代码 + 追踪                │
│         │                                                   │
│         ▼                                                   │
│  3. statistical-analysis ───► 正确统计 + APA 报告            │
│         │                                                   │
│         ▼                                                   │
│  4. data-visualization ─────► 出版质量图表                   │
│         │                                                   │
│         ▼                                                   │
│  5. latex-paper ────────────► 完整 LaTeX 论文                │
│         │                                                   │
│         ▼                                                   │
│  6. conference-submission ──► 投稿就绪文件包                  │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 组合技能的技巧

1. **连接相关技能**处理复杂任务：
   ```bash
   cat skills/latex-paper.md skills/academic-english.md > CLAUDE.md
   ```

2. **切换技能**随阶段推进：
   ```bash
   # 分析阶段
   cp skills/statistical-analysis.md CLAUDE.md

   # 写作阶段
   cp skills/latex-paper.md CLAUDE.md
   ```

3. **分层技能**获取全面指令：
   ```bash
   # 基础 + 特定
   cat skills/latex-paper.md skills/conference-submission.md > CLAUDE.md
   ```

4. **维护主文件**包含所有定制技能：
   ```bash
   cat skills/*.md > .cursorrules
   ```
