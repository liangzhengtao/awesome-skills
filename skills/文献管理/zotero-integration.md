# Zotero 文献管理集成

> Category: 文献管理 | Difficulty: beginner | Last updated: 2026

## When to Use

当用户需要使用 Zotero 管理参考文献、导出 BibTeX、组织文献库或与其他工具集成时使用此技能。适用于文献收集、引用管理、团队协作等场景。当用户提及 Zotero、文献管理、BibTeX 导出、reference manager、文献库整理、citation key 或 bibliography 时触发。

## Instructions for AI Assistant

### 基本原则

1. **自动化优先**：善用 Zotero 的自动抓取和同步功能
2. **规范命名**：统一的 citation key 命名规则
3. **结构化组织**：使用集合和标签相结合的方式
4. **数据安全**：启用同步，防止数据丢失
5. **工具集成**：与 LaTeX 编辑器、笔记工具无缝配合

### BibTeX 导出工作流

#### 安装 Better BibTeX 插件

```markdown
## Better BibTeX 安装步骤

1. 访问 https://retorque.re/zotero-better-bibtex/installation/
2. 下载最新版 .xpi 文件
3. 在 Zotero 中：工具 → 插件 → 从文件安装
4. 重启 Zotero
5. 在设置中配置 citation key 格式
```

#### Citation Key 命名规范

```markdown
## Citation Key 格式设置

### 推荐格式
在 Better BibTeX 设置中配置 Citation Key 格式：

学术论文：
  [auth:lower][year][title:lower:nospace:select,1,1]

示例结果：
  smith2024attention
  chen2024efficient
  brown2020language

### 常用格式变量
  [auth]           → 作者姓（大写首字母）
  [auth:lower]     → 作者姓（全小写）
  [authorsN]       → 前N位作者
  [year]           → 发表年份
  [title:lower]    → 标题（小写）
  [title:lower:nospace:select,1,1] → 标题第一个词
  [veryshorttitle] → 简短标题
  [journal:lower]  → 期刊名

### 处理特殊情况
- 同年同作者多篇：加后缀 a, b, c
  格式: [auth:lower][year][title:lower:nospace:select,1,1]:[year>0?+duplicate(letter)]

- 多作者（>3）使用 et al:
  格式: [authEtAl:lower][year][veryshorttitle:lower]

- 机构作者：
  格式: [authors1:lower][year][veryshorttitle:lower]
```

#### 自动导出设置

```markdown
## 自动导出 BibTeX

### 方法1：自动导出到固定路径
1. 右键点击要导出的集合
2. 选择 "Export Collection..."
3. 格式选择 "Better BibTeX"
4. 勾选 "Keep updated"
5. 选择导出路径（如项目目录下的 references.bib）

### 方法2：按需导出
在 LaTeX 项目中使用：
  \bibliography{references}

在 Zotero 中导出：
  文件 → 导出文献库 → Better BibTeX → 选择文件

### 方法3：命令行自动同步
安装 zotero-cli：
  npm install -g zotero-cli

配置同步脚本：
```bash
#!/bin/bash
# sync_zotero.sh
zotero-cli export --format "Better BibTeX" \
  --output /path/to/project/references.bib \
  --collection "MyProject"
```
```

### 文献库组织策略

#### 集合（Collection）结构

```
📚 My Library
├── 📂 Research Topics
│   ├── 📂 Topic A - Federated Learning
│   │   ├── 📂 Foundations
│   │   ├── 📂 Privacy Mechanisms
│   │   └── 📂 Applications
│   ├── 📂 Topic B - Medical Imaging
│   │   ├── 📂 Segmentation
│   │   └── 📂 Classification
│   └── 📂 Topic C - NLP
├── 📂 Courses
│   ├── 📂 CS229 - Machine Learning
│   └── 📂 CS231n - Deep Learning
├── 📂 To Read
│   ├── 📂 Priority High
│   ├── 📂 Priority Medium
│   └── 📂 Priority Low
├── 📂 Methodology
│   ├── 📂 Statistical Methods
│   ├── 📂 Deep Learning Architectures
│   └── 📂 Evaluation Metrics
└── 📂 Published
    ├── 📂 My Papers
    └── 📂 Cited in Paper 1
```

#### 标签（Tag）体系

```markdown
## 标签分类规范

### 方法标签 (Method)
- #method/transformer
- #method/cnn
- #method/gnn
- #method/reinforcement-learning
- #method/contrastive-learning

### 状态标签 (Status)
- #status/to-read
- #status/reading
- #status/read
- #status/summarized
- #status/cited

### 评价标签 (Quality)
- #quality/must-read
- #quality/seminal
- #quality/survey
- #quality/incremental

### 主题标签 (Topic)
- #topic/federated-learning
- #topic/medical-imaging
- #topic/privacy

### 方法论标签 (Methodology)
- #method/ablation-study
- #method/benchmark
- #method/survey
```

### 笔记模板

#### Zotero 内置笔记模板

```markdown
## 文献阅读笔记模板

### 基本信息
- **Title**: [论文标题]
- **Authors**: [作者列表]
- **Year**: [年份]
- **Venue**: [期刊/会议]
- **DOI**: [DOI]

### 一句话总结
[用一句话描述这篇论文的核心贡献]

### 研究问题
- RQ1: [研究问题1]
- RQ2: [研究问题2]

### 方法概述
[2-3 句话描述主要方法]

### 关键创新点
1. [创新点1]
2. [创新点2]
3. [创新点3]

### 实验结果
- 数据集: [使用了哪些数据集]
- 指标: [评估指标]
- 主要结果: [关键数值]
- 对比基线: [基线方法]

### 优势与局限
**Strengths:**
- [优势1]
- [优势2]

**Weaknesses:**
- [局限1]
- [局限2]

### 与我的研究相关性
- [如何启发我的工作]
- [可以借鉴的方法]
- [可以作为对比基线]

### 关键引用
- [值得追踪的参考文献]

### 阅读日期
[YYYY-MM-DD]
```

#### Zotero Integration with Obsidian

```markdown
## Zotero + Obsidian 集成

### 安装插件
1. Obsidian: 安装 "Zotero Integration" 插件
2. Zotero: 确保 Better BibTeX 已安装
3. 配置 Zotero 端口（默认 23119）

### Obsidian 模板（用于自动导入）

```markdown
---
title: "{{title}}"
authors: "{{authors}}"
year: {{year}}
citekey: "{{citekey}}"
DOI: "{{DOI}}"
tags:
  - paper
  - {{collection}}
---

# {{title}}

**Authors**: {{authors}}
**Year**: {{year}}
**Venue**: {{publicationTitle}}

## Abstract
{{abstract}}

## Key Contributions
- 

## Method
- 

## Results
- 

## My Notes
- 

## References
{{bibliography}}
```

### 使用方式
在 Obsidian 中：
1. Ctrl+P → "Zotero Integration: Create Note"
2. 选择要导入的文献
3. 自动生成笔记并链接到 Zotero
```

### 协作设置

```markdown
## Zotero 团队协作

### 方案1：Zotero Groups
1. 创建 Group Library
   - 登录 zotero.org → Groups → Create Group
   - 设置权限（Private / Public / Open）
2. 邀请团队成员
3. 共享文献库

优点: 官方支持，实时同步
缺点: 免费版 300MB 存储限制

### 方案2：共享文件夹同步
1. 使用 WebDAV 或云盘存储 PDF
2. 配置 Zotero 同步 → 文件同步 → WebDAV
   - 常用 WebDAV: 坚果云、NextCloud
3. 文献库数据用 Zotero 官方同步

### 方案3：共享 BibTeX 文件
1. 在 Git 仓库中维护 .bib 文件
2. 使用 Better BibTeX 自动导出
3. CI/CD 中验证 .bib 格式

```bash
# .gitlab-ci.yml
bib-check:
  script:
    - bibtex-tidy references.bib --sort=key --duplicates
```
```

### 常用工作流

#### 从浏览器到论文

```
浏览器 → Zotero Connector 一键保存
  ↓
Zotero 自动抓取元数据
  ↓
Zotero 自动下载 PDF（如有权限）
  ↓
分类到对应集合 + 添加标签
  ↓
阅读并添加笔记和高亮
  ↓
Better BibTeX 自动生成 citation key
  ↓
自动导出 .bib 文件到项目目录
  ↓
LaTeX 中使用 \cite{key} 引用
```

#### 批量导入

```python
# 使用 Zotero API 批量导入
import requests

ZOTERO_API = "https://api.zotero.org/users/{user_id}"
HEADERS = {"Zotero-API-Key": "your_api_key"}

def import_from_doi(doi, collection_key=None):
    """通过 DOI 导入文献"""
    import_data = {
        "items": [{
            "itemType": "journalArticle",
            "DOI": doi
        }]
    }
    if collection_key:
        url = f"{ZOTERO_API}/collections/{collection_key}/items"
    else:
        url = f"{ZOTERO_API}/items"

    response = requests.post(url, json=import_data, headers=HEADERS)
    return response.json()

def get_all_items(collection_key=None):
    """获取所有文献条目"""
    url = f"{ZOTERO_API}/items"
    if collection_key:
        url = f"{ZOTERO_API}/collections/{collection_key}/items"

    response = requests.get(url, headers=HEADERS, params={"limit": 100})
    return response.json()
```

## Templates

### 快速文献导入脚本模板

```bash
#!/bin/bash
# 从 DOI 列表批量导入到 Zotero
while IFS= read -r doi; do
  zotero-cli create --item "{\"itemType\":\"journalArticle\",\"DOI\":\"${doi}\"}"
  echo "Imported: ${doi}"
  sleep 1  # 避免 API 限流
  done < doi_list.txt
```

### Zotero + LaTeX 联动 Makefile 模板

```makefile
# Makefile - Zotero 自动同步 + LaTeX 编译
BIB_FILE = references.bib
ZOTERO_COLLECTION = MyProject

sync-bib:
	zotero-cli export --format "Better BibTeX" \
	  --output $(BIB_FILE) --collection "$(ZOTERO_COLLECTION)"

paper: sync-bib
	pdflatex main.tex
	bibtex main
	pdflatex main.tex
	pdflatex main.tex

clean:
	rm -f *.aux *.bbl *.blg *.log *.out
```

### 文献速读笔记模板

```markdown
**Key**: [citekey]
**Question**: [这篇论文回答什么问题？]
**Approach**: [核心方法，2-3句]
**Result**: [最关键的实验数字]
**Gap**: [与我的研究之间的差距]
**Action**: [ ] 引用  [ ] 作为基线  [ ] 借鉴方法  [ ] 不相关
```

## Common Patterns

### BibTeX 整理

```bash
# 使用 bibtex-tidy 整理 .bib 文件
bibtex-tidy references.bib \
  --sort=key \
  --duplicates=key,doi \
  --remove-empty-fields \
  --encode-urls \
  --wrap=80 \
  --no-remove-dupe-fields \
  --output references_tidy.bib
```

### Citation Key 一致性检查

```python
import re

def validate_citation_keys(bib_file):
    """检查 BibTeX citation key 命名规范"""
    pattern = re.compile(r'@(\w+)\{([^,]+),')
    issues = []

    with open(bib_file, 'r') as f:
        content = f.read()

    for match in pattern.finditer(content):
        entry_type, key = match.groups()
        # 检查格式: lowercase + year + word
        if not re.match(r'^[a-z]+\d{4}[a-z]+$', key):
            issues.append(f"Non-standard key: {key}")
        # 检查是否有大写字母
        if key != key.lower():
            issues.append(f"Uppercase in key: {key}")

    if issues:
        print("Issues found:")
        for issue in issues:
            print(f"  - {issue}")
    else:
        print("All citation keys follow the convention.")

    return issues
```

## Pitfalls to Avoid

1. **不同步**：未启用 Zotero 同步导致数据丢失
2. **citation key 不一致**：每次导出都重新生成 key，导致 LaTeX 引用失效（使用 Better BibTeX 的 pin 功能）
3. **PDF 元数据错误**：自动抓取的元数据可能有误，需要手动核实
4. **重复条目**：同一论文多次导入产生重复（使用 Duplicate Items 工具合并）
5. **标签混乱**：标签过多或命名不规范导致无法有效筛选
6. **忽略版本兼容**：Zotero 6 和 7 的插件不兼容，升级前确认插件支持

## Resources

- [Zotero 官方文档](https://www.zotero.org/support/)
- [Better BibTeX 文档](https://retorque.re/zotero-better-bibtex/)
- [Zotero API 文档](https://www.zotero.org/support/dev/web_api/v3/start)
- [Zotero + Obsidian 集成指南](https://github.com/mgmeyers/obsidian-zotero-integration)
- [bibtex-tidy](https://flamingtempura.github.io/bibtex-tidy/)
