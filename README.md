<div align="center">

# 🧪 Awesome Skills

### AI Coding Assistant Skills for Researchers

**[English](#english) | [中文](#中文)**

<br/>

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/Skills-12-orange)](#skills-table)

<br/>

### 🎯 Stop explaining your research workflow to AI every time.<br/>Write the skill once. Get perfect results forever.

</div>

---

<a name="english"></a>

## 🇬🇧 English

### 💡 What is this?

**Awesome Skills** is a curated collection of [AI coding assistant skills](https://kimi.ai) — reusable instruction files that teach your AI assistant how to perform research tasks *exactly* the way you want.

Instead of writing the same prompt over and over, you write a **skill once** — and your AI assistant follows it perfectly every single time.

---

### 😤 Before vs After

<table>
<tr>
<th width="50%">❌ Without Skills</th>
<th width="50%">✅ With Skills</th>
</tr>
<tr>
<td>

**You:** "Help me write a LaTeX paper"

**AI:**
- Generates generic LaTeX template
- Missing `\usepackage` for your field
- No journal-specific formatting
- Citations in wrong format
- Figures not properly referenced

*You spend 30 min fixing everything...*

</td>
<td>

**You:** "Write my paper using `latex-paper` skill"

**AI:**
- Uses your target journal's exact template
- Correct citation format (APA/IEEE/Nature)
- Proper `\label` and `\ref` for all figures
- Statistical tests reported correctly
- Code compiles without errors on first try

*Ready to submit in 5 min* ✨

</td>
</tr>
<tr>
<td>

**You:** "Analyze this CSV data"

**AI:**
- Runs basic `describe()` and a bar chart
- No normality test, no effect size
- Missing confidence intervals
- Wrong statistical test for your data type
- You redo the entire analysis manually

</td>
<td>

**You:** "Analyze using `statistical-analysis` skill"

**AI:**
- Checks data distribution first
- Selects correct test (parametric vs non-parametric)
- Reports effect sizes and CIs
- Generates publication-quality figures
- Outputs APA-formatted results section

</td>
</tr>
</table>

---

### 🚀 Quick Start

Skills are just **instruction files** that tell your AI assistant how to behave. Drop them into your project and your AI will follow the instructions automatically.

#### Cursor (.cursorrules)

```bash
# Copy skill to your project root
cp skills/latex-paper.md .cursorrules

# Or append to existing rules
cat skills/latex-paper.md >> .cursorrules
```

#### Claude Code (CLAUDE.md)

```bash
# Copy skill to your project root
cp skills/latex-paper.md CLAUDE.md

# Or append to existing instructions
cat skills/latex-paper.md >> CLAUDE.md
```

#### Kimi Code (AGENTS.md)

```bash
# Copy skill to your project root
cp skills/latex-paper.md AGENTS.md

# Or append to existing instructions
cat skills/latex-paper.md >> AGENTS.md
```

> 💡 **Pro tip:** You can combine multiple skills by concatenating them into a single file!

---

<a name="skills-table"></a>

### 📚 Skills Catalog

#### 📝 Academic Writing / 学术写作

| Skill | Description | Use When |
|-------|-------------|----------|
| [`latex-paper`](skills/latex-paper.md) | LaTeX paper writing with journal-specific formatting | Writing journal or conference papers |
| [`research-proposal`](skills/research-proposal.md) | Grant and thesis proposal writing | Applying for funding or writing thesis proposals |
| [`literature-review`](skills/literature-review.md) | Systematic literature review and synthesis | Reviewing a research field or writing related work |
| [`academic-english`](skills/academic-english.md) | Academic English polishing and grammar | Polishing non-native English writing |

#### 📊 Data Analysis / 数据分析

| Skill | Description | Use When |
|-------|-------------|----------|
| [`statistical-analysis`](skills/statistical-analysis.md) | Statistical testing with proper assumptions checks | Analyzing experimental data |
| [`data-visualization`](skills/data-visualization.md) | Publication-quality figures (matplotlib/seaborn/plotly) | Creating figures for papers |
| [`ml-experiment`](skills/ml-experiment.md) | ML experiment tracking with proper baselines | Running machine learning experiments |

#### 📖 Literature Management / 文献管理

| Skill | Description | Use When |
|-------|-------------|----------|
| [`zotero-integration`](skills/zotero-integration.md) | Zotero bibliography integration | Managing references with Zotero |
| [`citation-management`](skills/citation-management.md) | Citation formatting across styles | Formatting references for different journals |

#### 🔬 Experiment Tools / 实验工具

| Skill | Description | Use When |
|-------|-------------|----------|
| [`jupyter-notebook`](skills/jupyter-notebook.md) | Clean Jupyter notebook workflows | Running and organizing notebooks |
| [`docker-reproducibility`](skills/docker-reproducibility.md) | Reproducible research environments | Setting up reproducible experiments |

#### 📬 Paper Submission / 论文投稿

| Skill | Description | Use When |
|-------|-------------|----------|
| [`conference-submission`](skills/conference-submission.md) | Conference submission checklist and formatting | Submitting to NeurIPS, ICML, CVPR, etc. |

---

### 🎬 Usage Examples

#### Example 1: Writing a Full Paper

```bash
# 1. Load the latex-paper skill
cp skills/latex-paper.md CLAUDE.md

# 2. Ask your AI assistant
"Write a LaTeX paper for IEEE TPAMI on my transformer attention mechanism.
Include: abstract, introduction, related work, method, experiments, conclusion.
Use IEEE citation format. Reference figures as Fig. 1, Fig. 2, etc."
```

#### Example 2: Analyzing Experiment Data

```bash
# 1. Load the statistical-analysis skill
cp skills/statistical-analysis.md .cursorrules

# 2. Ask your AI assistant
"Analyze the data in results.csv. Compare model A vs model B performance.
Check normality, run appropriate tests, report effect sizes and CIs.
Generate a box plot for Figure 1."
```

#### Example 3: Complete Research Workflow

See [`examples/research-workflow.md`](examples/research-workflow.md) for a full end-to-end workflow combining multiple skills.

---

### ❓ FAQ

<details>
<summary><b>Q: What AI assistants do these skills work with?</b></summary>

These skills work with any AI coding assistant that supports custom instructions:
- [Cursor](https://cursor.sh) via `.cursorrules`
- [Claude Code](https://claude.ai/code) via `CLAUDE.md`
- [Kimi Code](https://kimi.ai) via `AGENTS.md`
- [Windsurf](https://windsurf.ai) via `.windsurfrules`
- [Cline](https://github.com/cline/cline) via `.clinerules`
- [Aider](https://aider.chat) via `.aider.conf.yml`
- Any assistant that reads instruction files

</details>

<details>
<summary><b>Q: Can I combine multiple skills?</b></summary>

Yes! Simply concatenate the skill files:

```bash
cat skills/latex-paper.md skills/data-visualization.md > CLAUDE.md
```

Or use them selectively based on your current task.

</details>

<details>
<summary><b>Q: How are these different from just writing prompts?</b></summary>

Skills are:
- **Persistent** — saved in your project, not lost between sessions
- **Version-controlled** — track changes with git
- **Reusable** — share with your team
- **Composable** — combine multiple skills
- **Tested** — refined through real research workflows

</details>

<details>
<summary><b>Q: Can I modify the skills for my field?</b></summary>

Absolutely! Skills are just markdown files. Fork this repo and customize them for your specific research area, journal requirements, or lab conventions.

</details>

<details>
<summary><b>Q: Do these skills work for non-English papers?</b></summary>

Yes! Skills like `latex-paper` and `academic-english` can be configured for Chinese (中文), Japanese (日本語), and other languages. See each skill's documentation for language options.

</details>

---

### 🔗 See Also

- 🤖 [awesome-ai-rules](https://github.com/nicekate/awesome-ai-rules) — Curated collection of AI coding assistant rules and configurations
- ✅ [vibe-check](https://github.com/nicekate/vibe-check) — Validate your AI assistant's output quality
- 🔄 [ai-commit](https://github.com/nicekate/commit-ai) (commit-ai) — AI-powered conventional commit messages
- 🔌 [awesome-mcp-servers](https://github.com/nicekate/awesome-mcp-servers) — Model Context Protocol server collection

---

### 🤝 Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Ways to contribute:**
- 🆕 Add a new skill for your research area
- 🐛 Fix bugs or improve existing skills
- 📖 Improve documentation
- 💡 Suggest new skill ideas via [Issues](https://github.com/liangzhengtao/awesome-skills/issues)

---

### 📄 License

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

---

<div align="center">

**[⬆ Back to top](#-awesome-skills)**

---

<a name="中文"></a>

</div>

## 🇨🇳 中文

### 💡 这是什么？

**Awesome Skills** 是一个精选的 [AI 编程助手技能](https://kimi.ai)合集——可复用的指令文件，教会你的 AI 助手*完全按照你想要的方式*执行研究任务。

你不需要每次都写同样的提示词。**写一次技能**——AI 助手每次都会完美执行。

---

### 😤 使用前 vs 使用后

<table>
<tr>
<th width="50%">❌ 没有技能</th>
<th width="50%">✅ 有技能</th>
</tr>
<tr>
<td>

**你：** "帮我写一篇 LaTeX 论文"

**AI：**
- 生成通用的 LaTeX 模板
- 缺少你领域的 `\usepackage`
- 没有期刊特定格式
- 引用格式错误
- 图片没有正确引用

*你花了 30 分钟修正所有问题...*

</td>
<td>

**你：** "用 `latex-paper` 技能写论文"

**AI：**
- 使用目标期刊的精确模板
- 正确的引用格式（APA/IEEE/Nature）
- 所有图片有正确的 `\label` 和 `\ref`
- 统计检验正确报告
- 代码首次编译无错误

*5 分钟即可投稿* ✨

</td>
</tr>
<tr>
<td>

**你：** "分析这个 CSV 数据"

**AI：**
- 运行基本的 `describe()` 和柱状图
- 没有正态性检验，没有效应量
- 缺少置信区间
- 数据类型选错统计检验
- 你手动重新做整个分析

</td>
<td>

**你：** "用 `statistical-analysis` 技能分析"

**AI：**
- 先检查数据分布
- 选择正确的检验（参数 vs 非参数）
- 报告效应量和置信区间
- 生成出版质量的图表
- 输出 APA 格式的结果部分

</td>
</tr>
</table>

---

### 🚀 快速开始

技能只是**指令文件**，告诉你的 AI 助手如何行动。把它们放到你的项目中，AI 就会自动遵循指令。

#### Cursor (.cursorrules)

```bash
# 复制技能到项目根目录
cp skills/latex-paper.md .cursorrules

# 或追加到现有规则
cat skills/latex-paper.md >> .cursorrules
```

#### Claude Code (CLAUDE.md)

```bash
# 复制技能到项目根目录
cp skills/latex-paper.md CLAUDE.md

# 或追加到现有指令
cat skills/latex-paper.md >> CLAUDE.md
```

#### Kimi Code (AGENTS.md)

```bash
# 复制技能到项目根目录
cp skills/latex-paper.md AGENTS.md

# 或追加到现有指令
cat skills/latex-paper.md >> AGENTS.md
```

> 💡 **专业提示：** 你可以通过连接多个技能文件来组合使用！

---

### 📚 技能目录

#### 📝 学术写作 / Academic Writing

| 技能 | 描述 | 使用场景 |
|------|------|----------|
| [`latex-paper`](skills/latex-paper.md) | LaTeX 论文写作，支持期刊特定格式 | 撰写期刊或会议论文 |
| [`research-proposal`](skills/research-proposal.md) | 基金申请和学位论文开题报告 | 申请基金或撰写开题报告 |
| [`literature-review`](skills/literature-review.md) | 系统文献综述与综合 | 调研研究领域或撰写相关工作 |
| [`academic-english`](skills/academic-english.md) | 学术英语润色与语法修正 | 润色非母语英语写作 |

#### 📊 数据分析 / Data Analysis

| 技能 | 描述 | 使用场景 |
|------|------|----------|
| [`statistical-analysis`](skills/statistical-analysis.md) | 统计检验与假设验证 | 分析实验数据 |
| [`data-visualization`](skills/data-visualization.md) | 出版质量图表（matplotlib/seaborn/plotly） | 为论文创建图表 |
| [`ml-experiment`](skills/ml-experiment.md) | 机器学习实验追踪与基线对比 | 运行机器学习实验 |

#### 📖 文献管理 / Literature Management

| 技能 | 描述 | 使用场景 |
|------|------|----------|
| [`zotero-integration`](skills/zotero-integration.md) | Zotero 文献库集成 | 使用 Zotero 管理文献 |
| [`citation-management`](skills/citation-management.md) | 多格式引用管理 | 为不同期刊格式化引用 |

#### 🔬 实验工具 / Experiment Tools

| 技能 | 描述 | 使用场景 |
|------|------|----------|
| [`jupyter-notebook`](skills/jupyter-notebook.md) | 干净的 Jupyter Notebook 工作流 | 运行和组织 Notebook |
| [`docker-reproducibility`](skills/docker-reproducibility.md) | 可复现研究环境 | 搭建可复现实验环境 |

#### 📬 论文投稿 / Paper Submission

| 技能 | 描述 | 使用场景 |
|------|------|----------|
| [`conference-submission`](skills/conference-submission.md) | 会议投稿检查清单与格式化 | 投稿 NeurIPS、ICML、CVPR 等 |

---

### 🎬 使用示例

#### 示例 1：撰写完整论文

```bash
# 1. 加载 latex-paper 技能
cp skills/latex-paper.md CLAUDE.md

# 2. 向 AI 助手提问
"为 IEEE TPAMI 写一篇关于我的 Transformer 注意力机制的 LaTeX 论文。
包含：摘要、引言、相关工作、方法、实验、结论。
使用 IEEE 引用格式。图片引用格式为 Fig. 1, Fig. 2 等。"
```

#### 示例 2：分析实验数据

```bash
# 1. 加载 statistical-analysis 技能
cp skills/statistical-analysis.md .cursorrules

# 2. 向 AI 助手提问
"分析 results.csv 中的数据。对比模型 A 和模型 B 的性能。
检查正态性，运行合适的检验，报告效应量和置信区间。
生成图 1 的箱线图。"
```

#### 示例 3：完整研究工作流

参见 [`examples/research-workflow.md`](examples/research-workflow.md) 了解结合多个技能的完整端到端工作流。

---

### ❓ 常见问题

<details>
<summary><b>问：这些技能适用于哪些 AI 助手？</b></summary>

这些技能适用于任何支持自定义指令的 AI 编程助手：
- [Cursor](https://cursor.sh) 通过 `.cursorrules`
- [Claude Code](https://claude.ai/code) 通过 `CLAUDE.md`
- [Kimi Code](https://kimi.ai) 通过 `AGENTS.md`
- [Windsurf](https://windsurf.ai) 通过 `.windsurfrules`
- [Cline](https://github.com/cline/cline) 通过 `.clinerules`
- [Aider](https://aider.chat) 通过 `.aider.conf.yml`
- 任何读取指令文件的助手

</details>

<details>
<summary><b>问：可以组合多个技能吗？</b></summary>

可以！直接连接技能文件即可：

```bash
cat skills/latex-paper.md skills/data-visualization.md > CLAUDE.md
```

或根据当前任务选择性使用。

</details>

<details>
<summary><b>问：这些技能和直接写提示词有什么区别？</b></summary>

技能具有以下特点：
- **持久化** — 保存在项目中，不会在会话间丢失
- **版本控制** — 用 git 跟踪变更
- **可复用** — 与团队共享
- **可组合** — 组合多个技能
- **经过验证** — 通过真实研究工作流反复打磨

</details>

<details>
<summary><b>问：可以为我的领域修改技能吗？</b></summary>

当然可以！技能就是 markdown 文件。Fork 本仓库，根据你的研究方向、期刊要求或实验室规范进行定制。

</details>

<details>
<summary><b>问：这些技能支持非英语论文吗？</b></summary>

支持！`latex-paper` 和 `academic-english` 等技能可以配置为中文、日语等语言。详见各技能的文档说明。

</details>

---

### 🔗 相关项目

- 🤖 [awesome-ai-rules](https://github.com/nicekate/awesome-ai-rules) — AI 编程助手规则和配置精选合集
- ✅ [vibe-check](https://github.com/nicekate/vibe-check) — 验证 AI 助手输出质量
- 🔄 [ai-commit](https://github.com/nicekate/commit-ai)（commit-ai）— AI 驱动的约定式提交信息
- 🔌 [awesome-mcp-servers](https://github.com/nicekate/awesome-mcp-servers) — Model Context Protocol 服务器合集

---

### 🤝 贡献

欢迎贡献！请参阅 [CONTRIBUTING.md](CONTRIBUTING.md) 了解指南。

**贡献方式：**
- 🆕 为你的研究领域添加新技能
- 🐛 修复 bug 或改进现有技能
- 📖 改进文档
- 💡 通过 [Issues](https://github.com/liangzhengtao/awesome-skills/issues) 建议新技能

---

### 📄 许可证

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

---

<div align="center">

**[⬆ 回到顶部](#-awesome-skills)**

</div>
