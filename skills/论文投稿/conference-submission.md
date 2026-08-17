# 会议论文投稿

> Category: 论文投稿 | Difficulty: advanced | Last updated: 2026

## When to Use

当用户需要向学术会议投稿论文时使用此技能。适用于 NeurIPS、ICML、ICLR、ACL、EMNLP、CVPR、ICCV、ECCV、AAAI、IJCAI 等顶级 AI/ML/CV/NLP 会议的投稿准备。当用户提及会议投稿、conference submission、rebuttal、rebuttal writing、camera-ready、审稿回复、revision response 或 submission system 时触发。

## Instructions for AI Assistant

### 基本原则

1. **严格遵守截止日期**：提前至少 3 天开始准备提交
2. **格式符合要求**：严格按照会议模板排版
3. **匿名性**：双盲审稿需确保论文中不泄露作者信息
4. **完整性**：确保所有必要材料（论文、补充材料、代码）齐全
5. **质量优先**：宁可推迟投稿也不提交不成熟的论文

### 顶级会议信息速查

```markdown
## AI/ML 顶级会议速查表 (2026)

### 机器学习
| 会议 | 通常截稿 | 通知 | 会议 | 页数限制 | 双盲 |
|------|---------|------|------|---------|------|
| NeurIPS | 5月 | 9月 | 12月 | 9页(+无限参考) | 是 |
| ICML | 1月 | 5月 | 7月 | 8页(+无限参考) | 是 |
| ICLR | 9月/1月 | 11月/3月 | 5月 | 9页(+无限参考) | 是 |

### 计算机视觉
| 会议 | 通常截稿 | 通知 | 会议 | 页数限制 | 双盲 |
|------|---------|------|------|---------|------|
| CVPR | 11月 | 2月 | 6月 | 8页(+无限参考) | 是 |
| ICCV | 3月 | 7月 | 10月 | 8页(+无限参考) | 是 |
| ECCV | 3月 | 7月 | 10月 | 14页(LNCS) | 是 |

### 自然语言处理
| 会议 | 通常截稿 | 通知 | 会议 | 页数限制 | 双盲 |
|------|---------|------|------|---------|------|
| ACL | 1月 | 5月 | 7月 | 8页(+无限参考) | 是 |
| EMNLP | 6月 | 9月 | 11月 | 8页(+无限参考) | 是 |
| NAACL | 10月 | 2月 | 6月 | 8页(+无限参考) | 是 |

### 人工智能
| 会议 | 通常截稿 | 通知 | 会议 | 页数限制 | 双盲 |
|------|---------|------|------|---------|------|
| AAAI | 8月 | 11月 | 2月 | 7页(+无限参考) | 是 |
| IJCAI | 1月 | 4月 | 8月 | 7页(+无限参考) | 是 |

### 数据库/数据挖掘
| 会议 | 通常截稿 | 通知 | 会议 | 页数限制 | 双盲 |
|------|---------|------|------|---------|------|
| KDD | 2月 | 5月 | 8月 | 9页(+无限参考) | 是 |
| SIGMOD | 10月 | 2月 | 6月 | 12页(ACM) | 是 |
| WWW | 10月 | 1月 | 4月 | 12页(+无限参考) | 是 |

### 系统/网络
| 会议 | 通常截稿 | 通知 | 会议 | 页数限制 | 双盲 |
|------|---------|------|------|---------|------|
| OSDI | 5月/12月 | 8月/3月 | 11月/7月 | 12页 | 是 |
| SOSP | 4月 | 7月 | 10月 | 12页 | 是 |
| NSDI | 5月/9月 | 8月/12月 | 4月/7月 | 12页 | 是 |
```

### 投稿前检查清单

```markdown
## Pre-Submission Checklist

### 论文内容
- [ ] 标题简洁明确，能准确反映论文贡献
- [ ] 摘要在字数限制内（通常 150-300 词）
- [ ] 所有章节完整（Intro, Related Work, Method, Experiments, Conclusion）
- [ ] 贡献声明清晰（通常 3-4 条）
- [ ] 创新点突出且与现有工作明确区分
- [ ] 实验充分（多数据集、多基线、消融实验、统计检验）
- [ ] 局限性有讨论
- [ ] 参考文献完整且格式一致

### 格式要求
- [ ] 使用会议官方 LaTeX 模板
- [ ] 页数符合限制（不含参考文献）
- [ ] 字体大小符合要求（通常 10pt）
- [ ] 图片清晰可读（≥300 dpi）
- [ ] 表格数据对齐且无溢出

### 双盲要求
- [ ] 作者信息已移除
- [ ] \author{} 中使用匿名
- [ ] PDF 元数据中无作者信息
- [ ] 自引改为第三人称（"In our previous work [1]..." → "Smith et al. [1]..."）
- [ ] 致谢部分已移除
- [ ] 补充材料中无泄露信息
- [ ] GitHub 链接使用匿名仓库（如适用）

### 补充材料
- [ ] 代码（如有匿名 GitHub）
- [ ] 详细实验结果
- [ ] 证明/推导细节
- [ ] 额外可视化

### 提交系统
- [ ] 注册提交系统账号（OpenReview/CMT）
- [ ] 确认截止日期（注意时区！通常 AoE）
- [ ] 上传 PDF 并检查渲染效果
- [ ] 填写元数据（标题、摘要、作者、关键词）
- [ ] 选择主题领域 (Primary/Secondary Area)
- [ ] 确认无冲突审稿人
- [ ] 最终提交并确认
```

### 提交系统导航

#### OpenReview（NeurIPS/ICLR/ICML）

```markdown
## OpenReview 投稿流程

### 注册与设置
1. 访问 https://openreview.net
2. 使用机构邮箱注册（提升可信度）
3. 完善个人资料（机构、研究领域、发表记录）

### 创建投稿
1. 点击 "Submit a Paper"
2. 选择对应的会议/Workshop
3. 填写必填字段：
   - Title
   - Abstract（粘贴纯文本）
   - Authors（添加所有作者的 OpenReview ID）
   - Author Order（确认顺序）
   - Keywords（从预定义列表选择 3-5 个）
   - Primary Area（选择主要研究方向）
   - Secondary Area（可选）

### 上传文件
1. Paper（PDF，≤ 页数限制 + 参考文献）
2. Supplementary Material（ZIP，≤ 100MB）
3. Code（可选，匿名仓库）

### 特殊字段
- "Dual Submission" 声明（是否同时投其他会议）
- "Ethics Review" 问卷（如适用）
- "Reproducibility" 声明

### 最终检查
1. 预览 PDF 渲染效果
2. 检查作者信息是否正确隐藏
3. 确认所有作者都已同意提交
4. 点击 "Submit" 前再次确认截止时间

### 投稿后
- 关注 OpenReview 上的评论和审稿进度
- 准备 Rebuttal（如有机会）
- 根据审稿意见准备修改
```

#### CMT（ACL/EMNLP/AAAI）

```markdown
## CMT 投稿流程

### 注册
1. 访问 https://cmt3.research.microsoft.com
2. 使用 Microsoft 账号登录
3. 搜索对应会议并注册

### 提交步骤
1. "Create New Submission"
2. 填写 Title, Abstract, Keywords
3. 添加 Co-authors
4. 选择 Subject Areas（最多 3 个）
5. 上传论文 PDF
6. 上传补充材料（可选）
7. 声明冲突机构

### 注意事项
- CMT 通常有字数统计限制
- 某些会议使用 SoftConf 而非 CMT
- 注意提交按钮的确认步骤
```

### Rebuttal 写作指南

#### Rebuttal 整体策略

```markdown
## Rebuttal 写作策略

### 核心原则
1. **感谢审稿人**：开头表达感谢，展示专业态度
2. **逐点回应**：针对每位审稿人的每条意见逐一回复
3. **简洁有力**：通常只有 500-1000 词的空间，要精炼
4. **有理有据**：用数据和事实回应，而非空泛辩解
5. **知错能改**：承认合理的批评，说明修改计划
6. **突出共识**：指出多位审稿人认可的优点

### 时间管理
- 通常有 1-2 周的 rebuttal 窗口
- 第 1-2 天：分析所有审稿意见，分类整理
- 第 3-5 天：撰写 rebuttal 初稿
- 第 6-7 天：修改润色，运行补充实验（如可能）
- 第 8 天：最终检查并提交

### 结构模板
```
We thank all reviewers for their constructive feedback. Below we address
each concern. [Reviewer-specific responses follow.]

**Summary of Key Points:**
- Reviewers raised concerns about [共同问题1] and [共同问题2].
- R1 and R3 praised [公认优点].
- We have run additional experiments to address the concerns about [问题].
```
```

#### Rebuttal 逐点回应模板

```markdown
## Rebuttal 逐点回应格式

### 格式1：简洁版（推荐用于空间紧张时）

---

**[R1-Q1]** The reviewer questions whether the method scales to larger datasets.

**Response:** We appreciate this important question. We have now conducted
experiments on ImageNet-1K (1.28M images). Our method achieves 78.5% top-1
accuracy (+1.2% over baseline), demonstrating scalability. These results will
be included in the final version.

---

**[R1-Q2]** What is the computational overhead compared to Method X?

**Response:** Thank you for this question. Our method adds only 3.2%
training time overhead (Table A in revision). At inference, there is no
additional cost as [reason].

---

### 格式2：详细版（用于需要深入解释的情况）

---

**[R2-C1]** The novelty is incremental as similar ideas appear in [1].

**Response:** We respectfully disagree. While [1] shares [相似点], our work
differs fundamentally in three ways:
(1) **[区别1]**: Unlike [1], which [做法], we [创新做法] (see Section 3.2).
(2) **[区别2]**: [具体说明]
(3) **[区别3]**: [具体说明]
We will make this distinction more explicit in the revised Related Work.

---

**[R2-C2]** Missing comparison with [Method Y].

**Response:** Thank you for the suggestion. We have now added this comparison.
Our method outperforms [Method Y] by X.X% on Dataset A (see Table 1 in revision).
We will include these results in the camera-ready version.

---

### 格式3：承认不足并说明计划

---

**[R3-C1]** The writing could be improved in several places.

**Response:** We thank the reviewer for pointing this out. We will carefully
revise the paper for clarity, focusing on:
(1) Improving the notation consistency in Section 3.
(2) Adding a running example to illustrate [方法].
(3) Restructuring Section 4.2 for better flow.

---
```

#### 常见审稿意见的回应策略

```markdown
## 常见审稿意见回应

### "Novelty is limited / Incremental contribution"
策略：
1. 明确区分与最近工作 (even similar ones) 的区别
2. 强调理论贡献或实践影响
3. 列出具体的技术创新点
4. 可能需要新的分析来证明贡献

### "Experiments are not sufficient"
策略：
1. 如果能快速跑实验 → 补充结果放入 rebuttal
2. 如果不能 → 承诺在 camera-ready 补充
3. 具体说明将添加什么（数据集、基线、指标）

### "Missing references / Related work is incomplete"
策略：
1. 感谢审稿人指出遗漏的文献
2. 说明将补充到 Related Work
3. 简要说明新引用与本工作的关系

### "Writing quality needs improvement"
策略：
1. 承认并感谢指出
2. 承诺在 camera-ready 做全面润色
3. 如果空间允许，指出具体改进计划

### "Assumptions are not justified"
策略：
1. 提供理论支撑或引用支持该假设的文献
2. 如果假设确实限制性，讨论其适用范围
3. 考虑补充假设放松后的实验

### "Comparison is unfair / Cherry-picked baselines"
策略：
1. 如果确实是遗漏 → 补充实验
2. 如果是受限于资源 → 说明原因并讨论
3. 确保与所有 SOTA 方法对比
```

### Camera-Ready 准备

```markdown
## Camera-Ready 准备流程

### 1. 审稿反馈整理
- 整理所有审稿人和 AC (Area Chair) 的意见
- 区分必须修改和建议修改
- 制作修改清单

### 2. 论文修改
- [ ] 按审稿意见修改论文内容
- [ ] 恢复作者信息
- [ ] 添加致谢部分
- [ ] 更新参考文献
- [ ] 修复所有指出的错误
- [ ] 改善写作质量

### 3. 格式调整
- [ ] 使用 camera-ready 模板（通常与投稿模板略有不同）
- [ ] 移除匿名标记
- [ ] 确保版权信息正确
- [ ] 添加 DOI（如已分配）
- [ ] 检查所有交叉引用

### 4. 源文件准备
- [ ] LaTeX 源文件（.tex, .bib, figures/）
- [ ] 所有字体嵌入
- [ ] 图片文件单独打包
- [ ] 确保可编译

### 5. 版权和伦理
- [ ] 签署版权转让协议
- [ ] 确认无抄袭问题
- [ ] 处理任何伦理审查要求

### 6. 提交
- [ ] 上传最终 PDF
- [ ] 上传 LaTeX 源文件
- [ ] 填写最终元数据
- [ ] 确认提交
```

#### Camera-Ready LaTeX 设置

```latex
%% Camera-Ready 版本修改

%% 1. 移除匿名设置
% 投稿版:
\documentclass[review,anonymous]{acmart}
% Camera-ready 版:
\documentclass[sigconf]{acmart}

%% 2. 恢复作者信息
\author{Author One}
\affiliation{%
  \institution{University A}
  \city{City}
  \country{Country}}
\email{author1@university.edu}

\author{Author Two}
\affiliation{%
  \institution{University B}
  \city{City}
  \country{Country}}
\email{author2@university.edu}

%% 3. 添加致谢
\begin{acks}
This work was supported by [资助机构和项目号]. We thank the anonymous
reviewers for their valuable feedback. We also thank [同事名] for
helpful discussions.
\end{acks}

%% 4. 添加补充说明（如审稿人要求的修改）
% 在论文末尾或相应位置添加
% "Note: This paper has been revised to address reviewer feedback,
%  including [修改列表]."

%% 5. 最终编译检查
% pdflatex → bibtex → pdflatex → pdflatex
% 确保无 warning
```

### 修改回应信模板

```latex
% revision_response.tex
\documentclass[12pt]{article}
\usepackage[margin=1in]{geometry}
\usepackage{xcolor}
\usepackage{enumitem}
\usepackage{hyperref}
\usepackage{booktabs}

\newcommand{\reviewer}[1]{\subsection*{Reviewer #1}}
\newcommand{\response}[1]{\par\noindent\textbf{Response:} #1\par}
\newcommand{\change}[1]{\par\noindent\textit{Changes:} {\color{blue}#1}\par}
\newcommand{\quoteR}[1]{\begin{quote}\textit{``#1''}\end{quote}}
\newcommand{\todo}[1]{{\color{red}[TODO: #1]}}

\begin{document}

\title{Response to Reviewers -- [Paper ID]}
\author{[Anonymous for Review]}
\date{\today}
\maketitle

\section*{Summary of Major Changes}

We sincerely thank the reviewers for their constructive feedback.
The major revisions in this paper include:

\begin{enumerate}[label=(\arabic*)]
  \item \textbf{[修改主题1]}: [简述修改内容和位置]
  \item \textbf{[修改主题2]}: [简述修改内容和位置]
  \item \textbf{[修改主题3]}: [简述修改内容和位置]
\end{enumerate}

Below we address each reviewer's comments point by point.
All page/section references refer to the revised paper.

\vspace{1em}
\hrule
\vspace{1em}

\reviewer{1}

\quoteR{[审稿人意见1原文]}
\response{[回复内容]}
\change{[具体修改，引用论文中的位置]}

\quoteR{[审稿人意见2原文]}
\response{[回复内容]}
\change{[具体修改]}

\vspace{1em}
\hrule
\vspace{1em}

\reviewer{2}

\quoteR{[审稿人意见1原文]}
\response{[回复内容]}
\change{[具体修改]}

\end{document}
```

### Revision Response 模板

```markdown
## Revision Response (非 LaTeX 格式)

### To the Area Chair / Senior Program Chair

Dear AC,

We thank you and all reviewers for the constructive feedback on our
submission "[Paper Title]" (ID: XXXX). We have carefully addressed
each concern and made significant improvements to our paper.

Below we provide a summary of major changes followed by detailed
point-by-point responses.

### Summary of Changes
1. **[改动1]**: [描述] (see Section X, Page Y)
2. **[改动2]**: [描述] (see new Table X)
3. **[改动3]**: [描述] (see Appendix X)

### List of Changes by Section
| Section | Change | Page |
|---------|--------|------|
| Abstract | [描述] | 1 |
| Introduction | [描述] | 1-2 |
| Method | [描述] | 4 |
| Experiments | [描述] | 6-7 |
| Appendix | [新增] | 10-11 |

---

### Reviewer 1

**Score: X → We believe these changes address the main concerns.**

#### [意见1]: [缩写的意见]
**Response:** [回复]

#### [意见2]: [缩写的意见]
**Response:** [回复]

---

### Reviewer 2

...
```

### 会议特定注意事项

```markdown
## 会议特定要求

### NeurIPS
- 使用 neurips_YYYY.sty 模板
- Checklist 必须填写（Reproducibility Checklist）
- Ethics Review 问卷（如涉及）
- 9 正文 + 无限参考 + 无限附录
- OpenReview 提交

### ICML
- 使用 icmlYYYY.sty 模板
- 可选的 Reproducibility Checklist
- 8 正文 + 无限参考 + 无限附录
- OpenReview 提交

### ICLR
- 使用 iclr 模板
- 9 正文 + 无限参考
- OpenReview 公开审稿（通常）
- Rebuttal 期间可以看到其他审稿意见

### CVPR
- 使用 cvpr.sty 模板
- 8 正文 + 无限参考
- CMT 提交
- 双盲严格执行
- 需要 Supplementary Material

### ACL
- 使用 acl.sty 模板
- 8 正文 + 无限参考
- ARR (ACL Rolling Review) 或直接投稿
- 可选的 Ethics Statement
- Checklist 必填
```

### 投稿时间规划

```markdown
## 投稿时间规划（以截稿日前 8 周为例）

### T-8 周: 论文写作启动
- 完成实验主体
- 开始撰写 Method 和 Experiments 章节
- 整理图表

### T-6 周: 初稿完成
- 完成所有章节初稿
- 导师/合作者第一轮反馈
- 开始绘制正式图表

### T-4 周: 修改和补充
- 根据反馈修改
- 补充实验（如有遗漏）
- 检查 Related Work 完整性

### T-2 周: 打磨
- 全文润色（English polishing）
- 格式检查
- 双盲检查
- 让同事阅读并反馈

### T-1 周: 最终准备
- 最终修改
- 准备补充材料
- 检查提交系统要求
- 准备 Rebuttal 预案

### T-3 天: 提交
- 上传论文到提交系统
- 检查 PDF 渲染效果
- 填写元数据
- 确认无误后提交

### T-0: 截止
- 最后检查（截止前 2 小时）
- 确认提交成功
- 备份所有文件
```

## Templates

### Rebuttal 快速回应模板

```
**[R#-Q#]** Reviewer's concern in one sentence.

**Response:** We thank the reviewer. [Address with evidence/data].
Additional experiments show [result] (see Table X in revision).
```

### 投稿 Cover Letter 模板

```
Dear Program Chairs,

We submit our paper "[Title]" to [Conference].

This paper proposes [method], which addresses [problem].
Our main contributions are:
1. [Contribution 1]
2. [Contribution 2]
3. [Contribution 3]

We confirm this work is original, not under review elsewhere,
and all authors consent to the submission.

Sincerely,
[Authors]
```

### Camera-Ready 修改清单模板

```markdown
## Camera-Ready Changes
- [ ] Restore author names and affiliations
- [ ] Add acknowledgments section
- [ ] Incorporate reviewer-requested experiments/clarifications
- [ ] Update Related Work with suggested references
- [ ] Proofread entire paper
- [ ] Verify all figures are ≥300 dpi
- [ ] Check page count against final deadline requirements
```

## Common Patterns

### 增量修改法

```
不要在截稿前大幅重写论文。采用增量修改：
1. 骨架完成 → 各章节有基本内容
2. 内容填充 → 补充实验、添加引用
3. 打磨润色 → 语言、图表、格式
4. 最终检查 → checklist 逐项核对
```

### 快速预印本策略

```
如果论文被拒：
1. 分析审稿意见，识别核心问题
2. 必要时补充实验
3. 修改论文后投下一个会议
4. 可先上传 arXiv 保护优先权
5. 利用 arXiv 的时间戳作为证据
```

## Pitfalls to Avoid

1. **错过截止日期**：设多个提醒，考虑时区差异（AoE = UTC-12）
2. **匿名性泄露**：仔细检查 PDF 元数据、自引、代码仓库链接
3. **格式违规**：严格按模板，不要自行调整字号/边距
4. **页数超限**：正文页数不含参考文献和附录，但需确认具体规则
5. **双投违规**：确认会议是否允许同时投稿或预印本
6. **补充材料过大**：通常有大小限制（≤ 100MB），大文件使用链接
7. **Rebuttal 情绪化**：保持专业和礼貌，即使审稿意见不公正
8. **忽略 AC 意见**：Area Chair 的 meta-review 比个别审稿人更有决定权
9. **不检查 PDF**：提交前务必在不同设备上检查 PDF 渲染效果
10. **最后时刻提交**：系统可能因高负载崩溃，提前至少 1 天提交

## Resources

- [OpenReview](https://openreview.net/)
- [Microsoft CMT](https://cmt3.research.microsoft.com/)
- [ACL Rolling Review (ARR)](https://aclrollingreview.org/)
- [Papers With Code - Conference Deadlines](https://paperswithcode.com/conferences)
- [AI Conference Deadlines](https://aideadlin.es/)
- [Rebuttal Writing Guide - NeurIPS](https://neurips.cc/)
- [How to Write a Good Rebuttal - cs.cmu.edu](http://www.cs.cmu.edu/~./hovy/)
- [Conference Paper Writing Tips - Stanford CS](https://cs.stanford.edu/)
