# LaTeX 学术论文写作

> Category: 学术写作 | Difficulty: intermediate | Last updated: 2026

## When to Use

当用户需要撰写、排版或修改 LaTeX 格式的学术论文时使用此技能。适用于 IEEE、ACM、Elsevier、Springer 等主流学术期刊和会议的论文模板。当用户提及 LaTeX、论文排版、BibTeX 引用、数学公式排版或学术写作格式化时触发。

## Instructions for AI Assistant

### 基本原则

1. **始终使用模板**：不要从零开始创建论文，优先使用目标期刊/会议的官方模板
2. **保持一致性**：全文使用统一的引用格式、图表编号风格和术语
3. **可编译性**：确保生成的 LaTeX 代码可以直接编译，避免语法错误
4. **包管理精简**：只引入必要的宏包，避免包冲突

### 论文结构模板

#### IEEE 双栏格式

```latex
\documentclass[conference]{IEEEtran}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage{amsmath,amssymb,amsfonts}
\usepackage{graphicx}
\usepackage{textcomp}
\usepackage{xcolor}
\usepackage{booktabs}
\usepackage{multirow}
\usepackage{hyperref}
\usepackage{cite}
\usepackage{algorithm}
\usepackage{algorithmic}

\begin{document}

\title{Your Paper Title Here}

\author{
\IEEEauthorblockN{Author One\IEEEauthorrefmark{1},
Author Two\IEEEauthorrefmark{1},
Author Three\IEEEauthorrefmark{2}}
\IEEEauthorblockA{\IEEEauthorrefmark{1}Department of Computer Science, University A\\
Email: \{author1, author2\}@university-a.edu}
\IEEEauthorblockA{\IEEEauthorrefmark{2}Institute of AI, University B\\
Email: author3@university-b.edu}
}

\maketitle

\begin{abstract}
% 150-250 words for IEEE
% Problem → Method → Result → Contribution
Your abstract here.
\end{abstract}

\begin{IEEEkeywords}
keyword1, keyword2, keyword3, keyword4, keyword5
\end{IEEEkeywords}

\section{Introduction}
\label{sec:intro}

\section{Related Work}
\label{sec:related}

\section{Methodology}
\label{sec:method}

\section{Experiments}
\label{sec:experiments}

\section{Discussion}
\label{sec:discussion}

\section{Conclusion}
\label{sec:conclusion}

\bibliographystyle{IEEEtran}
\bibliography{references}

\end{document}
```

#### ACM 格式

```latex
\documentclass[sigconf,review,anonymous]{acmart}

\usepackage{booktabs}
\usepackage{subcaption}

\AtBeginDocument{%
  \providecommand\BibTeX{{%
    Bib\TeX}}}

\copyrightyear{2026}
\acmYear{2026}
\setcopyright{acmlicensed}
\acmConference[Conference Name '26]{Full Conference Name}{Month Day--Day, 2026}{City, Country}
\acmBooktitle{Proceedings of Conference Name '26}
\acmDOI{10.1145/xxxxxxx.xxxxxxx}
\acmISBN{978-x-xxxx-xxxx-x/xx/xx}

\begin{document}

\title{Your Paper Title Here}

\author{Author One}
\affiliation{%
  \institution{University A}
  \city{City}
  \country{Country}}
\email{author1@university-a.edu}

\begin{abstract}
Your abstract here.
\end{abstract}

\begin{CCSXML}
<ccs2012>
  <concept>
    <concept_id>10010147.10010178</concept_id>
    <concept_desc>Computing methodologies~Artificial intelligence</concept_desc>
    <concept_significance>500</concept_significance>
  </concept>
</ccs2012>
\end{CCSXML}

\ccsdesc[500]{Computing methodologies~Artificial intelligence}

\keywords{keyword1, keyword2, keyword3}

\maketitle

\section{Introduction}
\label{sec:intro}

% ... rest of paper

\bibliographystyle{ACM-Reference-Format}
\bibliography{references}

\end{document}
```

#### Elsevier 格式

```latex
\documentclass[preprint,12pt]{elsarticle}

\usepackage{lineno}
\usepackage{amsmath}
\usepackage{graphicx}
\usepackage{booktabs}
\usepackage{hyperref}

\modulolinenumbers[5]

\journal{Journal Name Here}

\begin{document}

\begin{frontmatter}

\title{Your Paper Title Here}

\author[aff1]{Author One\corref{cor1}}
\ead{author1@university.edu}
\author[aff1,aff2]{Author Two}

\cortext[cor1]{Corresponding author}
\affiliation[aff1]{organization={Department of CS, University A},
                     city={City},
                     country={Country}}
\affiliation[aff2]{organization={Institute of AI, Lab B},
                     city={City},
                     country={Country}}

\begin{abstract}
Your abstract here (150-300 words).
\end{abstract}

\begin{graphicalabstract}
% \includegraphics{grabs}
\end{graphicalabstract}

\begin{highlights}
\item Highlight 1: Key finding or contribution
\item Highlight 2: Novel method or approach
\item Highlight 3: Significant experimental result
\end{highlights}

\begin{keyword}
keyword1 \sep keyword2 \sep keyword3 \sep keyword4
\end{keyword}

\end{frontmatter}

\linenumbers

\section{Introduction}
\label{sec:intro}

% ... rest of paper

\bibliographystyle{elsarticle-num}
\bibliography{references}

\end{document}
```

### BibTeX 引用模式

#### references.bib 常用条目类型

```bibtex
% 期刊论文
@article{smith2024attention,
  author    = {Smith, John and Doe, Jane and Zhang, Wei},
  title     = {Attention Mechanisms in Deep Learning: A Comprehensive Survey},
  journal   = {IEEE Transactions on Neural Networks and Learning Systems},
  volume    = {35},
  number    = {3},
  pages     = {1234--1250},
  year      = {2024},
  publisher = {IEEE},
  doi       = {10.1109/TNNLS.2024.1234567}
}

% 会议论文
@inproceedings{chen2024transformer,
  author    = {Chen, Xiaoming and Li, Hua},
  title     = {Efficient Transformer Architectures for Low-Resource Languages},
  booktitle = {Proceedings of the 62nd Annual Meeting of the ACL (ACL 2024)},
  year      = {2024},
  pages     = {1523--1535},
  address   = {Bangkok, Thailand},
  publisher = {Association for Computational Linguistics},
  doi       = {10.18653/v1/2024.acl-long.83}
}

% 书籍
@book{goodfellow2016deep,
  author    = {Goodfellow, Ian and Bengio, Yoshua and Courville, Aaron},
  title     = {Deep Learning},
  publisher = {MIT Press},
  year      = {2016},
  address   = {Cambridge, MA},
  isbn      = {978-0262035613}
}

% 技术报告/预印本
@article{vaswani2017attention,
  author  = {Vaswani, Ashish and Shazeer, Noam and Parmar, Niki and
             Uszkoreit, Jakob and Jones, Llion and Gomez, Aidan N. and
             Kaiser, {\L}ukasz and Polosukhin, Illia},
  title   = {Attention Is All You Need},
  journal = {Advances in Neural Information Processing Systems},
  volume  = {30},
  year    = {2017}
}

% arXiv 预印本
@article{brown2020gpt3,
  author        = {Brown, Tom B. and Mann, Benjamin and Ryder, Nick and others},
  title         = {Language Models are Few-Shot Learners},
  journal       = {arXiv preprint arXiv:2005.14165},
  year          = {2020},
  eprint        = {2005.14165},
  archiveprefix = {arXiv},
  primaryclass  = {cs.CL}
}
```

#### 引用键命名规范

```
格式: {第一作者姓}{年份}{标题关键词}
示例:
  smith2024attention     → Smith 2024 年关于 attention 的文章
  chen2024transformer    → Chen 2024 年关于 transformer 的文章
  openai2023gpt4         → OpenAI 2023 年的 GPT-4 论文
```

### 数学公式模板

```latex
% 行内公式
The loss function $\mathcal{L}(\theta)$ is minimized during training.

% 行间公式（无编号）
\[
\mathcal{L}(\theta) = -\sum_{i=1}^{N} y_i \log \hat{y}_i + (1-y_i) \log(1-\hat{y}_i)
\]

% 行间公式（有编号）
\begin{equation}
\label{eq:attention}
\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V
\end{equation}

% 多行对齐公式
\begin{align}
\mathbf{h}_t &= \text{GRU}(\mathbf{x}_t, \mathbf{h}_{t-1}) \label{eq:gru} \\
\hat{y}_t &= \text{softmax}(\mathbf{W}_o \mathbf{h}_t + \mathbf{b}_o) \label{eq:output}
\end{align}

% 分段函数
\begin{equation}
\text{ReLU}(x) = \begin{cases}
x & \text{if } x > 0 \\
0 & \text{otherwise}
\end{cases}
\end{equation}

% 矩阵
\begin{equation}
\mathbf{W} = \begin{pmatrix}
w_{11} & w_{12} & \cdots & w_{1n} \\
w_{21} & w_{22} & \cdots & w_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
w_{m1} & w_{m2} & \cdots & w_{mn}
\end{pmatrix}
\end{equation}

% 定理环境
\newtheorem{theorem}{Theorem}
\newtheorem{lemma}[theorem]{Lemma}
\newtheorem{corollary}[theorem]{Corollary}
\newtheorem{definition}{Definition}

\begin{theorem}
\label{thm:convergence}
Let $f: \mathbb{R}^n \to \mathbb{R}$ be $L$-smooth and $\mu$-strongly convex.
Then gradient descent with step size $\eta = \frac{2}{L+\mu}$ satisfies:
\begin{equation}
f(\mathbf{x}_{t+1}) - f(\mathbf{x}^*) \leq \left(\frac{L-\mu}{L+\mu}\right)^2 [f(\mathbf{x}_t) - f(\mathbf{x}^*)]
\end{equation}
\end{theorem}
```

### 图表格式

#### 图片插入

```latex
% 单图
\begin{figure}[t]
  \centering
  \includegraphics[width=\linewidth]{figures/architecture.pdf}
  \caption{Overview of the proposed architecture. The model consists of
           three main components: encoder, attention module, and decoder.}
  \label{fig:architecture}
\end{figure}

% 子图
\begin{figure*}[t]
  \centering
  \begin{subfigure}[b]{0.32\textwidth}
    \includegraphics[width=\textwidth]{figures/result_a.pdf}
    \caption{Dataset A}
    \label{fig:result_a}
  \end{subfigure}
  \hfill
  \begin{subfigure}[b]{0.32\textwidth}
    \includegraphics[width=\textwidth]{figures/result_b.pdf}
    \caption{Dataset B}
    \label{fig:result_b}
  \end{subfigure}
  \hfill
  \begin{subfigure}[b]{0.32\textwidth}
    \includegraphics[width=\textwidth]{figures/result_c.pdf}
    \caption{Dataset C}
    \label{fig:result_c}
  \end{subfigure}
  \caption{Comparison of results across three datasets. Best viewed in color.}
  \label{fig:results}
\end{figure*}
```

#### 表格模板

```latex
\begin{table}[t]
  \centering
  \caption{Comparison with state-of-the-art methods on benchmark dataset.}
  \label{tab:comparison}
  \begin{tabular}{lccc}
    \toprule
    \textbf{Method} & \textbf{Accuracy (\%)} & \textbf{F1 Score} & \textbf{Params (M)} \\
    \midrule
    Baseline A       & 85.2 $\pm$ 0.3        & 0.842 $\pm$ 0.004 & 12.3 \\
    Baseline B       & 87.1 $\pm$ 0.2        & 0.865 $\pm$ 0.003 & 18.7 \\
    Baseline C       & 88.4 $\pm$ 0.4        & 0.878 $\pm$ 0.005 & 24.1 \\
    \midrule
    \textbf{Ours}    & \textbf{91.3 $\pm$ 0.2} & \textbf{0.908 $\pm$ 0.002} & 15.6 \\
    \bottomrule
  \end{tabular}
\end{table}
```

### 算法伪代码

```latex
\begin{algorithm}[t]
\caption{Training Procedure}
\label{alg:training}
\begin{algorithmic}[1]
\REQUIRE Training data $\mathcal{D} = \{(\mathbf{x}_i, y_i)\}_{i=1}^N$,
         learning rate $\eta$, epochs $E$
\ENSURE Trained model parameters $\theta^*$
\STATE Initialize parameters $\theta$ randomly
\FOR{epoch $= 1$ to $E$}
  \STATE Shuffle $\mathcal{D}$
  \FOR{each mini-batch $\mathcal{B} \subset \mathcal{D}$}
    \STATE Compute loss $\mathcal{L}(\theta; \mathcal{B})$
    \STATE Compute gradients $\nabla_\theta \mathcal{L}$
    \STATE Update $\theta \leftarrow \theta - \eta \nabla_\theta \mathcal{L}$
  \ENDFOR
  \STATE Evaluate on validation set
  \IF{validation loss not improved for $p$ epochs}
    \STATE Early stopping
  \ENDIF
\ENDFOR
\RETURN $\theta^*$
\end{algorithmic}
\end{algorithm}
```

### 常用 LaTeX 宏包

| 宏包 | 用途 | 示例 |
|------|------|------|
| `amsmath` | 数学公式 | `\usepackage{amsmath}` |
| `graphicx` | 图片插入 | `\usepackage{graphicx}` |
| `booktabs` | 专业表格 | `\usepackage{booktabs}` |
| `hyperref` | 超链接 | `\usepackage[colorlinks=true]{hyperref}` |
| `cleveref` | 智能引用 | `\cref{fig:arch}`, `\cref{eq:loss}` |
| `algorithm2e` | 算法排版 | `\usepackage[linesnumbered]{algorithm2e}` |
| `subcaption` | 子图 | `\usepackage{subcaption}` |
| `xcolor` | 颜色支持 | `\usepackage{xcolor}` |
| `tikz` | 矢量绘图 | `\usepackage{tikz}` |
| `siunitx` | 单位排版 | `\SI{95.3}{\percent}` |
| `natbib` | 灵活引用 | `\citet{}`, `\citep{}` |

### 审稿回复模板

```latex
% 在回复信中使用
\documentclass[12pt]{article}
\usepackage[margin=1in]{geometry}
\usepackage{xcolor}
\usepackage{enumitem}

\newcommand{\reviewer}[1]{\subsection*{Reviewer \##1}}
\newcommand{\response}[1]{\textbf{Response:} #1}
\newcommand{\change}[1]{\textit{Changes made:} \textcolor{blue}{#1}}
\newcommand{\quoteR}[1]{\begin{quote}\textit{``#1''}\end{quote}}

\begin{document}

\title{Response to Reviewers}
\author{Author Names}
\date{\today}
\maketitle

\section*{Summary of Changes}

We thank the reviewers for their constructive feedback. The main revisions include:
\begin{enumerate}[label=(\arabic*)]
  \item Added ablation study (Section~4.5)
  \item Expanded related work discussion (Section~2)
  \item Clarified experimental setup
  \item Fixed typos and improved writing quality
\end{enumerate}

\reviewer{1}

\quoteR{The authors should provide more details about the experimental setup.}

\response{We appreciate this suggestion. We have expanded the experimental
setup section with additional details.}
\change{See Section~3.2, paragraphs 2-4, where we now describe the hardware
configuration, software versions, and hyperparameter search space.}

\quoteR{What is the computational cost of the proposed method?}

\response{Thank you for this important question. We have added a comprehensive
computational analysis in Table~3.}
\change{See the new Table~3 and the discussion in Section~4.6.}

\end{document}
```

## Templates

### 审稿回复快速模板

```latex
% 快速回应审稿人的 3 行模板
\reviewer{N}
\quoteR{审稿人意见原文}
\response{回应内容}
\change{具体修改位置和内容}
```

### 新论文项目初始化脚本

```bash
#!/bin/bash
# init_paper.sh - 初始化 LaTeX 论文项目
CONFERENCE=$1
mkdir -p paper/figures paper/sections
cp templates/${CONFERENCE}/*.sty paper/
cp templates/${CONFERENCE}/*.cls paper/
touch paper/references.bib
echo "\\input{sections/introduction}" > paper/main.tex
echo "Project initialized for ${CONFERENCE}"
```

### BibTeX 自动补全模板

```bibtex
@article{key_template,
  author    = {Last1, First1 and Last2, First2},
  title     = {Title in Sentence Case},
  journal   = {Journal Name},
  year      = {YYYY},
  volume    = {},
  number    = {},
  pages     = {},
  doi       = {10.XXXX/XXXXX}
}
```

## Common Patterns

### 论文写作流程

1. **确定目标期刊/会议** → 下载官方模板
2. **搭建骨架** → 先写各节标题和要点
3. **填充内容** → Introduction → Method → Experiments → Related Work → Conclusion
4. **精修 Abstract** → 最后写，精炼全文贡献
5. **参考文献** → 使用 BibTeX 管理，确保格式一致
6. **编译检查** → 确保无 warning，交叉引用正确

### 图片引用规范

```latex
% 正确：引用标签而非硬编码编号
As shown in Figure~\ref{fig:architecture}, the model...   % ✓
As shown in Figure 3, the model...                         % ✗

% 使用 ~ 防止断行
Table~\ref{tab:comparison}                                 % ✓
Section~\ref{sec:method}                                   % ✓
Equation~\eqref{eq:attention}                              % ✓
```

### 交叉引用最佳实践

```latex
% 使用 cleveref 包自动处理引用前缀
\usepackage{cleveref}
\cref{fig:arch}          % → Figure 1
\cref{tab:comparison}    % → Table 1
\cref{eq:attention}      % → Equation (1)
\cref{sec:method}        % → Section 3
\Cref{fig:arch}          % → Figure 1 (句首大写)
\cref{fig:arch,fig:results} % → Figures 1 and 2
```

## Pitfalls to Avoid

1. **不要使用 `\begin{center}` 在浮动体内居中**：使用 `\centering` 代替，避免额外间距
2. **不要硬编码编号**：始终使用 `\label` 和 `\ref` 进行交叉引用
3. **图片格式**：优先使用 PDF/EPS/SVG 矢量图，避免 PNG/JPG 位图（除照片外）
4. **宏包冲突**：`hyperref` 通常应最后加载（少数例外如 `cleveref` 在 `hyperref` 之后）
5. **IEEEtran 模板中不要使用 `\footnote`**：使用 `\thanks` 代替
6. **数学模式中的文本**：使用 `\text{}` 而非直接输入文本
7. **表格中避免竖线**：使用 `booktabs` 的 `\toprule`、`\midrule`、`\bottomrule`
8. **编译顺序**：使用 BibTeX 时需执行 `pdflatex → bibtex → pdflatex → pdflatex`

## Resources

- [Overleaf 学术模板库](https://www.overleaf.com/latex/templates)
- [CTAN - LaTeX 宏包文档](https://ctan.org/)
- [LaTeX Wikibook](https://en.wikibooks.org/wiki/LaTeX)
- [Detexify - 手写识别 LaTeX 符号](http://detexify.kirelabs.org/)
- [IEEE Template Selector](https://journals.ieeeauthorcenter.ieee.org/create-your-ieee-journal-article/authoring-tools-and-ieee-templates/)
- [ACM Primary Article Templates](https://www.acm.org/publications/proceedings-template)
- [Elsevier LaTeX Instructions](https://www.elsevier.com/researcher/author/policies-and-guidelines/latex-instructions)
