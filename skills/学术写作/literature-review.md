# 文献综述写作

> Category: 学术写作 | Difficulty: intermediate | Last updated: 2026

## When to Use

当用户需要进行系统性文献调研、撰写文献综述（Literature Review）或相关工作（Related Work）章节时使用此技能。适用于开题报告、综述论文、学位论文第二章、研究计划书中的文献回顾部分。当用户提及文献综述、literature review、related work、系统综述、systematic review、survey 或 meta-analysis 时触发。

## Instructions for AI Assistant

### 基本原则

1. **系统性**：搜索策略应可复现，覆盖全面
2. **批判性**：不是简单罗列，而是分析、比较、评价
3. **结构性**：按主题/方法/时间线组织，逻辑清晰
4. **时效性**：重点关注近 5 年文献，经典文献不限
5. **可追溯**：每条论述有明确引用来源

### 文献搜索策略

#### 搜索框架（PICO/PIO）

```
P (Population/Problem)  → 研究对象/问题领域
I (Intervention/Interest) → 关注的方法/技术/干预
C (Comparison)           → 对比方法（可选）
O (Outcome)              → 关注的结果/指标

示例：
P: 医疗图像分割
I: 基于 Transformer 的方法
C: 与 CNN 方法对比
O: Dice 系数和推理速度
```

#### 搜索词构建

```
步骤1：提取核心概念
  "深度学习 医疗图像分割" → {deep learning, medical image segmentation}

步骤2：同义词/近义词扩展
  deep learning → "neural network" OR "convolutional neural network" OR "CNN"
  medical image → "medical imaging" OR "clinical image" OR "biomedical image"
  segmentation → "semantic segmentation" OR "instance segmentation"

步骤3：组合搜索式
  (deep learning OR neural network OR CNN) AND
  (medical image OR medical imaging OR clinical) AND
  (segmentation OR semantic segmentation)

步骤4：限制条件
  时间：2020-2026
  语言：English
  类型：Journal article, Conference paper
```

#### 数据库选择

| 数据库 | 适用领域 | 特点 |
|--------|----------|------|
| **Google Scholar** | 全学科 | 覆盖最广，适合初始搜索 |
| **Web of Science** | 自然科学/社会科学 | 高质量索引，支持引文分析 |
| **Scopus** | 全学科 | 最大的摘要和引文数据库 |
| **PubMed** | 生物医学 | 医学文献首选 |
| **IEEE Xplore** | 电子/计算机 | IEEE 和 IET 出版物 |
| **ACM DL** | 计算机科学 | ACM 出版物 |
| **arXiv** | 预印本 | 最新研究，未经同行评审 |
| **DBLP** | 计算机科学 | 计算机科学文献目录 |
| **CNKI** | 中文文献 | 中文学术文献首选 |
| **万方数据** | 中文文献 | 中文期刊和学位论文 |

### PRISMA 流程图

```
┌─────────────────────────────────┐
│        Identification           │
├─────────────────────────────────┤
│ 数据库搜索记录: n = XXX          │
│ 其他来源发现:    n = XXX          │
│ 去重后:         n = XXX          │
└────────────┬────────────────────┘
             │
             ▼
┌─────────────────────────────────┐
│          Screening              │
├─────────────────────────────────┤
│ 筛选标题和摘要:  n = XXX         │
│ 排除:           n = XXX          │
│   - 不相关主题:  n = XXX         │
│   - 非目标文献:  n = XXX         │
└────────────┬────────────────────┘
             │
             ▼
┌─────────────────────────────────┐
│       Eligibility               │
├─────────────────────────────────┤
│ 全文评估:       n = XXX          │
│ 排除:           n = XXX          │
│   - 无实验结果:  n = XXX         │
│   - 重复发表:    n = XXX         │
│   - 质量不达标:  n = XXX         │
└────────────┬────────────────────┘
             │
             ▼
┌─────────────────────────────────┐
│         Included                │
├─────────────────────────────────┤
│ 最终纳入:       n = XXX          │
│   - 定性综合:    n = XXX         │
│   - 定量综合:    n = XXX (可选)  │
└─────────────────────────────────┘
```

#### PRISMA LaTeX 模板

```latex
\usepackage{tikz}
\usetikzlibrary{shapes.geometric, arrows}

\tikzstyle{process} = [rectangle, minimum width=3cm, minimum height=1cm,
                       text centered, draw=black, fill=blue!10]
\tikzstyle{arrow} = [thick,->,>=stealth]

\begin{tikzpicture}[node distance=1.5cm]
  \node (id1) [process] {数据库搜索: n = 500};
  \node (id2) [process, below of=id1] {去重后: n = 380};
  \node (scr1) [process, below of=id2] {标题/摘要筛选: n = 380};
  \node (scr2) [process, below of=scr1] {全文评估: n = 120};
  \node (inc) [process, below of=scr2] {最终纳入: n = 45};

  \draw [arrow] (id1) -- (id2);
  \draw [arrow] (id2) -- (scr1);
  \draw [arrow] (scr1) -- (scr2);
  \draw [arrow] (scr2) -- (inc);
\end{tikzpicture}
```

### 关键评价框架

#### 纳入/排除标准

```markdown
## Inclusion Criteria
- 发表时间：2018-2026年
- 语言：英文或中文
- 研究类型：实验研究、准实验研究
- 包含量化实验结果
- 发表在同行评审期刊或顶级会议

## Exclusion Criteria
- 综述/社论/短文/摘要
- 无实验验证的纯理论文章
- 样本量 < 30（如适用）
- 发表在掠夺性期刊
```

#### 质量评估清单

```markdown
## Quality Assessment Checklist (per paper)

### 研究设计 (0-3分)
- [ ] 研究问题明确 (0/1)
- [ ] 方法适合研究问题 (0/1)
- [ ] 实验设计合理 (0/1)

### 数据与样本 (0-3分)
- [ ] 数据来源描述清楚 (0/1)
- [ ] 样本量充足 (0/1)
- [ ] 数据预处理方法合理 (0/1)

### 结果与分析 (0-3分)
- [ ] 统计方法正确 (0/1)
- [ ] 结果报告完整 (0/1)
- [ ] 局限性充分讨论 (0/1)

### 可复现性 (0-1分)
- [ ] 代码/数据公开可用 (0/1)

总分：0-10分，≥7分纳入高质量研究
```

### 综述结构模板

#### 综述论文结构

```markdown
# A Survey on [Topic]: Methods, Applications, and Future Directions

## Abstract

## 1. Introduction
   - 背景与动机
   - 综述范围与目标
   - 与现有综述的区别
   - 贡献声明（3-4条）
   - 文章结构

## 2. Background and Preliminaries
   - 基本概念定义
   - 问题形式化
   - 历史发展脉络

## 3. Taxonomy of Methods
   ### 3.1 Category A: [方法类别1]
     #### 3.1.1 Representative Methods
     #### 3.1.2 Variants and Extensions
   ### 3.2 Category B: [方法类别2]
   ### 3.3 Category C: [方法类别3]

## 4. Datasets and Benchmarks
   ### 4.1 Common Datasets
   ### 4.2 Evaluation Metrics
   ### 4.3 Benchmark Results

## 5. Applications
   ### 5.1 Application Domain 1
   ### 5.2 Application Domain 2

## 6. Open Challenges and Future Directions
   ### 6.1 Technical Challenges
   ### 6.2 Application Challenges
   ### 6.3 Ethical Considerations

## 7. Conclusion

## References
```

#### Related Work 章节结构

```markdown
## 2. Related Work

### 2.1 [研究方向1]
[2-3段，分析该方向的代表性工作]
Existing works in this direction can be categorized into two groups.
The first group focuses on [方面A]. For example, Author et al. (Year)
proposed [方法]，achieving [效果]. However, [局限性]。Author et al.
(Year) addressed this limitation by [改进]，but [仍然存在的问题]。

The second group emphasizes [方面B]...

### 2.2 [研究方向2]
...

### 2.3 Summary
Table 1 summarizes the key differences between existing methods and
our approach. Unlike previous works, our method [核心区别]。
```

### 综合分析方法

#### 方法对比表

```latex
\begin{table*}[t]
\centering
\caption{Comparison of existing approaches for [task].}
\label{tab:comparison}
\resizebox{\textwidth}{!}{%
\begin{tabular}{lcccccc}
\toprule
\textbf{Method} & \textbf{Year} & \textbf{Type} & \textbf{Supervision}
  & \textbf{Real-time} & \textbf{SOTA Result} & \textbf{Code} \\
\midrule
Method A \cite{ref1} & 2020 & CNN & Fully    & Yes  & 85.3 & \checkmark \\
Method B \cite{ref2} & 2021 & GNN & Semi     & No   & 87.1 & \ding{55}  \\
Method C \cite{ref3} & 2023 & TF  & Self     & Yes  & 89.5 & \checkmark \\
\textbf{Ours}       & 2026 & --- & Self     & Yes  & \textbf{92.1} & \checkmark \\
\bottomrule
\end{tabular}%
}
\end{table*}
```

#### 发展趋势分析

```markdown
The evolution of [研究领域] can be divided into three phases:

**Phase 1 (2015-2018): Traditional Methods.**
Early approaches relied on [传统方法]，such as [例子].
These methods achieved [效果] but suffered from [局限性].

**Phase 2 (2018-2022): Deep Learning Era.**
The introduction of [技术] revolutionized the field. Key works include
[代表作1], which [贡献], and [代表作2], which [贡献].

**Phase 3 (2022-Present): Foundation Models.**
Recent work has shifted toward [趋势]，exemplified by [代表作].
This paradigm shift enables [能力] while presenting new challenges
in [方面].
```

### 引用管理最佳实践

```markdown
## Citation Dos and Don'ts

### Do:
- 每个重要论述都应有引用支撑
- 引用原始论文而非二次引用
- 平衡引用数量（避免过度自引）
- 包含最新文献（近2年）

### Don't:
- 不要罗列引用而无分析
  ✗ "Many methods have been proposed [1-20]."
  ✓ "Existing approaches can be grouped into three categories:
      supervised [1-5], unsupervised [6-12], and semi-supervised [13-20]."
- 不要只引用支持自己观点的文献
- 不要忽略反对意见和竞争方法
```

#### 引用密度参考

| 文献类型 | 建议引用数 | 说明 |
|----------|-----------|------|
| 综述论文 | 100-300+ | 覆盖全面 |
| 会议论文 | 25-40 | 精选引用 |
| 期刊论文 | 40-80 | 适当深入 |
| Related Work 章节 | 20-50 | 集中引用 |
| 博士论文文献综述 | 80-200 | 系统全面 |

### 搜索记录模板

```markdown
## Literature Search Log

### Search Session 1: 2026-01-15
- **Database**: Web of Science
- **Search Query**: ("federated learning" OR "collaborative learning")
    AND ("privacy" OR "differential privacy") AND "healthcare"
- **Filters**: 2020-2026, Article, English
- **Results**: 87 papers
- **Screened**: 87 → Included: 23
- **Notes**: Most papers focus on horizontal FL; vertical FL
  underrepresented

### Search Session 2: 2026-01-16
- **Database**: PubMed
- **Search Query**: federated learning medical data privacy
- **Filters**: 2020-2026
- **Results**: 134 papers
- **Screened**: 134 → Included: 31
- **Notes**: Good coverage of clinical applications
```

## Templates

### 单篇文献笔记模板

```markdown
**Citation**: Author et al. (Year). Title. Venue.
**Relevance**: ★★★★☆
**One-line summary**: [一句话概括核心贡献]
**Method**: [方法简述]
**Key results**: [主要实验结果]
**Limitations**: [不足之处]
**Relevance to my work**: [与我研究的关联]
```

### 文献对比分析表模板

```markdown
| 维度 | 方法 A | 方法 B | 方法 C | 本文 |
|------|--------|--------|--------|------|
| 核心思想 | | | | |
| 技术路线 | | | | |
| 数据集 | | | | |
| 主要指标 | | | | |
| 优势 | | | | |
| 局限 | | | | |
```

### 综述段落写作模板

```
[主题句] 现有 [方向] 的研究可分为三类。[句群1] 第一类聚焦于 [方面A]，
代表工作如 [作者A] 提出 [方法A]，实现了 [效果]，但 [局限]。[句群2]
第二类关注 [方面B]... [总结句] 综上，现有研究在 [空白] 方面仍有不足，
本文将 [如何填补]。
```

## Common Patterns

### 文献综述写作流程

```
1. 定义范围 → 确定主题边界和时间范围
2. 系统搜索 → 至少使用 3 个数据库
3. 筛选纳入 → 按标准筛选，记录 PRISMA 流程
4. 质量评估 → 使用标准清单评估每篇文献
5. 数据提取 → 提取关键信息到表格
6. 综合分析 → 按主题/方法分类综合
7. 撰写综述 → 从整体到细节，批判性分析
8. 更新迭代 → 定期补充最新文献
```

### 批判性分析模板

```markdown
## Critical Analysis Template

### Paper: [Author et al. (Year) - Title]

**Strengths:**
- [优势1]
- [优势2]

**Weaknesses:**
- [不足1]
- [不足2]

**Relevance to my research:**
- [相关度和启示]

**Quality Score:** X/10
```

## Pitfalls to Avoid

1. **"购物清单"式综述**：避免简单罗列 "A 做了 X，B 做了 Y"，应分析比较和综合
2. **遗漏关键文献**：搜索至少 3 个数据库，检查关键论文的引用链
3. **缺乏批判性**：不仅要描述方法，还要分析优缺点
4. **结构混乱**：按主题/方法/时间组织，避免随机排列
5. **引用不规范**：确保每个引用都可追溯，避免二手引用
6. **忽略灰色文献**：技术报告、预印本、学位论文也可能包含重要工作
7. **更新不及时**：综述完成后应再次搜索最新文献
8. **偏见**：避免只引用支持自己假设的文献

## Resources

- [PRISMA Statement](http://www.prisma-statement.org/)
- [Cochrane Handbook for Systematic Reviews](https://training.cochrane.org/handbook)
- [How to Write a Systematic Review - AMSTAR 2](https://amstar.ca/)
- [Rayyan - 系统综述筛选工具](https://www.rayyan.ai/)
- [Zotero - 文献管理](https://www.zotero.org/)
- [Publish or Perish - 引用分析工具](https://harzing.com/resources/publish-or-perish)
