# Contributing to Awesome Skills

**[English](#english) | [中文](#中文)**

Thank you for your interest in contributing! This guide will help you add new skills or improve existing ones.

<a name="english"></a>

## 🇬🇧 English

### How to Add a New Skill

#### 1. Create the Skill File

Create a new markdown file in the `skills/` directory:

```
skills/
└── your-skill-name.md
```

#### 2. Follow the Skill Template

Every skill file **must** include these sections:

```markdown
# Skill Name

## Description
Brief description of what this skill does and when to use it.

## Instructions
The actual instructions for the AI assistant. Be specific and detailed.

## Examples
Show example prompts and expected outputs.

## Configuration
Any configurable options (language, citation style, etc.)

## Notes
Additional notes, limitations, or tips.
```

#### 3. Quality Checklist

Before submitting, ensure your skill:

- [ ] Has a clear, descriptive name
- [ ] Includes all required sections (Description, Instructions, Examples, Configuration, Notes)
- [ ] Provides specific, actionable instructions (not vague guidance)
- [ ] Works with multiple AI assistants (Cursor, Claude Code, Kimi Code)
- [ ] Has been tested with at least one real research task
- [ ] Includes examples with sample input/output
- [ ] Does not contain sensitive information (API keys, credentials)
- [ ] Uses consistent formatting and clear language

#### 4. Update the README

Add your skill to the appropriate category table in `README.md`.

#### 5. Submit a Pull Request

1. Fork this repository
2. Create a feature branch: `git checkout -b add-skill/your-skill-name`
3. Commit your changes: `git commit -m "feat: add your-skill-name skill"`
4. Push to the branch: `git push origin add-skill/your-skill-name`
5. Open a Pull Request

### Skill Naming Convention

- Use lowercase with hyphens: `my-skill-name.md`
- Be descriptive: `statistical-analysis.md` not `stats.md`
- Match the category when possible: `latex-paper.md`, `ml-experiment.md`

### Code of Conduct

Please read our [Code of Conduct](CODE_OF_CONDUCT.md) before contributing.

---

<a name="中文"></a>

## 🇨🇳 中文

### 如何添加新技能

#### 1. 创建技能文件

在 `skills/` 目录下创建新的 markdown 文件：

```
skills/
└── your-skill-name.md
```

#### 2. 遵循技能模板

每个技能文件**必须**包含以下部分：

```markdown
# 技能名称

## 描述
简要描述这个技能做什么以及何时使用。

## 指令
给 AI 助手的实际指令。要具体和详细。

## 示例
展示示例提示词和期望输出。

## 配置
任何可配置选项（语言、引用格式等）。

## 说明
附加说明、限制或提示。
```

#### 3. 质量检查清单

提交前，请确保你的技能：

- [ ] 有清晰、描述性的名称
- [ ] 包含所有必需部分（描述、指令、示例、配置、说明）
- [ ] 提供具体、可操作的指令（不是模糊的指导）
- [ ] 适用于多个 AI 助手（Cursor、Claude Code、Kimi Code）
- [ ] 至少用一个真实研究任务测试过
- [ ] 包含带有示例输入/输出的示例
- [ ] 不包含敏感信息（API 密钥、凭据）
- [ ] 使用一致的格式和清晰的语言

#### 4. 更新 README

将你的技能添加到 `README.md` 中相应的分类表格中。

#### 5. 提交 Pull Request

1. Fork 本仓库
2. 创建功能分支：`git checkout -b add-skill/your-skill-name`
3. 提交更改：`git commit -m "feat: add your-skill-name skill"`
4. 推送到分支：`git push origin add-skill/your-skill-name`
5. 打开 Pull Request

### 技能命名规范

- 使用小写加连字符：`my-skill-name.md`
- 要有描述性：`statistical-analysis.md` 而不是 `stats.md`
- 尽量匹配分类：`latex-paper.md`、`ml-experiment.md`

### 行为准则

贡献前请阅读我们的[行为准则](CODE_OF_CONDUCT.md)。
