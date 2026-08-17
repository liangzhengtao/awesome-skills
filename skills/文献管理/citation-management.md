# 引用格式管理

> Category: 文献管理 | Difficulty: intermediate | Last updated: 2026

## When to Use

当用户需要了解不同引用格式、在不同引用风格之间转换、生成参考文献列表或验证引用格式时使用此技能。适用于论文写作中的引用管理、参考文献格式化、跨工具引用同步等场景。当用户提及引用格式、citation style、参考文献格式、APA/IEEE/Chicago 格式、GB/T 7714、BibTeX 格式转换、bibliography generation 或 citation verification 时触发。

## Instructions for AI Assistant

### 基本原则

1. **遵循目标期刊/会议要求**：始终先确认投稿目标的引用格式要求
2. **一致性**：全文使用统一的引用风格
3. **完整性**：每条引用信息必须完整（作者、标题、年份、页码等）
4. **准确性**：核实 DOI、页码、出版信息的准确性
5. **工具辅助**：使用自动化工具减少手动格式化

### 主要引用格式详解

#### 1. APA 7th Edition（美国心理学会）

```markdown
## APA 7th Edition 格式规范

### 文内引用 (In-text Citation)
单作者: (Smith, 2024) 或 Smith (2024) 指出...
双作者: (Smith & Chen, 2024) 或 Smith and Chen (2024)
三作者+: (Smith et al., 2024) 或 Smith et al. (2024)
机构作者: (World Health Organization [WHO], 2024) → 后续 (WHO, 2024)
无日期: (Smith, n.d.)
直接引用: (Smith, 2024, p. 15)
多篇引用: (Smith, 2024; Chen, 2023; Li et al., 2025)

### 参考文献格式

期刊论文:
  Smith, J. A., Chen, W., & Li, H. (2024). Title of the article in sentence
  case. *Journal Name*, *15*(3), 123–145. https://doi.org/10.xxxx/xxxxx

会议论文:
  Smith, J. A., & Chen, W. (2024). Title of the conference paper. In
  *Proceedings of the Conference Name* (pp. 123–135). Publisher.
  https://doi.org/10.xxxx/xxxxx

书籍:
  Smith, J. A. (2024). *Title of the book* (2nd ed.). Publisher.

书籍章节:
  Smith, J. A. (2024). Title of the chapter. In W. Chen & H. Li (Eds.),
  *Title of the book* (pp. 123–145). Publisher.

网页:
  Smith, J. A. (2024, March 15). Title of the webpage. *Website Name*.
  https://www.example.com/page

预印本:
  Smith, J. A., & Chen, W. (2024). Title of the preprint. *arXiv*.
  https://arxiv.org/abs/2401.12345

### BibTeX 格式
```bibtex
@article{smith2024title,
  author  = {Smith, John A. and Chen, Wei and Li, Hua},
  title   = {Title of the Article in Sentence Case},
  journal = {Journal Name},
  year    = {2024},
  volume  = {15},
  number  = {3},
  pages   = {123--145},
  doi     = {10.xxxx/xxxxx}
}
```
```

#### 2. IEEE（电气与电子工程师协会）

```markdown
## IEEE 格式规范

### 文内引用
使用数字编号 [1], [2], [3]...
连续引用: [1]–[3] 或 [1, 2, 3]
句末引用: ...as shown in [1].
多次引用同一篇: [1, Theorem 3.2]

### 参考文献格式

期刊论文:
  [1] J. A. Smith, W. Chen, and H. Li, "Title of the article,"
      *IEEE Trans. Neural Netw. Learn. Syst.*, vol. 35, no. 3,
      pp. 1234–1250, Mar. 2024.

会议论文:
  [2] J. A. Smith and W. Chen, "Title of the paper," in *Proc.
      IEEE Conf. Comput. Vis. Pattern Recognit. (CVPR)*, Seattle,
      WA, USA, Jun. 2024, pp. 1234–1243.

书籍:
  [3] I. Goodfellow, Y. Bengio, and A. Courville, *Deep Learning*.
      Cambridge, MA, USA: MIT Press, 2016.

在线资源:
  [4] J. A. Smith, "Title of the webpage," 2024. [Online]. Available:
      https://www.example.com/page

### BibTeX 格式
```bibtex
@article{smith2024title,
  author  = {Smith, J. A. and Chen, W. and Li, H.},
  title   = {Title of the Article},
  journal = {IEEE Trans. Neural Netw. Learn. Syst.},
  year    = {2024},
  volume  = {35},
  number  = {3},
  pages   = {1234--1250},
  month   = {Mar.}
}
```
```

#### 3. Chicago（芝加哥格式）

```markdown
## Chicago 17th Edition 格式规范

### Author-Date 系统 (科学类)

文内引用: (Smith 2024, 123) 或 Smith (2024, 123)
参考文献: Smith, John A. 2024. "Title of the Article." Journal Name 15, no. 3: 123–145.

### Notes-Bibliography 系统 (人文类)

脚注: ¹ John A. Smith, "Title of the Article," Journal Name 15, no. 3 (2024): 123.
参考文献: Smith, John A. "Title of the Article." Journal Name 15, no. 3 (2024): 123–145.
```

#### 4. GB/T 7714-2015（中国国家标准）

```markdown
## GB/T 7714-2015 格式规范

### 顺序编码制 (Numeric)
文内引用: [1], [2], [3]

### 著者-出版年制 (Author-Date)
文内引用: (Smith, 2024) 或 Smith(2024)

### 参考文献类型标识
期刊 [J], 专著 [M], 学位论文 [D], 会议录 [C],
报告 [R], 标准 [S], 专利 [P], 汇编 [G],
网络 [EB/OL], 数据库 [DB], 计算机程序 [CP]

### 格式示例

期刊 [J]:
[1] SMITH J A, CHEN W, LI H. Title of the article[J].
    Journal Name, 2024, 15(3): 123-145.

专著 [M]:
[2] GOODFELLOW I, BENGIO Y, COURVILLE A. Deep learning[M].
    Cambridge: MIT Press, 2016: 100-150.

会议论文 [C]:
[3] SMITH J A, CHEN W. Title of the paper[C]//Proceedings of
    CVPR. Seattle: IEEE, 2024: 1234-1243.

学位论文 [D]:
[4] 张三. 基于深度学习的图像分割方法研究[D]. 北京: 清华大学, 2024.

网络文献 [EB/OL]:
[5] SMITH J A. Title of the webpage[EB/OL]. (2024-03-15)
    [2024-06-01]. https://www.example.com/page

### BibTeX 格式 (使用 gbt7714 宏包)
```latex
\usepackage[super,sort&compress]{gbt7714}
\bibliographystyle{gbt7714-numerical}  % 顺序编码制
% 或
\bibliographystyle{gbt7714-author-year}  % 著者-出版年制
```

```bibtex
@article{smith2024title,
  author  = {Smith, John A. and Chen, Wei and Li, Hua},
  title   = {Title of the Article},
  journal = {Journal Name},
  year    = {2024},
  volume  = {15},
  number  = {3},
  pages   = {123--145}
}
```
```

### 格式快速对比表

```markdown
## 引用格式对比速查

| 特征              | APA 7th    | IEEE       | Chicago    | GB/T 7714  |
|-------------------|-----------|------------|------------|------------|
| 文内格式          | 作者+年份  | 数字编号   | 脚注/作者年 | 数字/作者年 |
| 排序方式          | 字母顺序   | 引用顺序   | 字母顺序   | 引用顺序    |
| 作者名格式        | 姓, 名缩写 | 名缩写 姓  | 姓, 名     | 姓 名缩写  |
| 标题大小写        | Sentence   | Sentence   | Title      | Sentence   |
| 期刊名            | 斜体       | 缩写斜体   | 斜体       | 正常        |
| DOI               | 必须       | 推荐       | 推荐       | 可选        |
| 主要领域          | 社科/心理  | 工程/CS    | 人文/历史  | 中文学术    |
```

### 跨引用格式转换

#### Python 脚本：BibTeX 格式检查和转换

```python
import re
import bibtexparser
from bibtexparser.bparser import BibTexParser
from bibtexparser.bwriter import BibTexWriter

def load_bib(file_path):
    """加载 BibTeX 文件"""
    with open(file_path) as f:
        parser = BibTexParser(common_strings=True)
        parser.ignore_nonstandard_types = False
        return bibtexparser.load(f, parser)

def check_completeness(entries):
    """检查引用条目的完整性"""
    required_fields = {
        'article': ['author', 'title', 'journal', 'year'],
        'inproceedings': ['author', 'title', 'booktitle', 'year'],
        'book': ['author', 'title', 'publisher', 'year'],
        'misc': ['author', 'title', 'year'],
    }

    issues = []
    for entry in entries:
        entry_type = entry.get('ENTRYTYPE', 'misc').lower()
        required = required_fields.get(entry_type, ['author', 'title', 'year'])

        for field in required:
            if field not in entry or not entry[field].strip():
                issues.append(
                    f"  [{entry['ID']}] Missing required field: {field}"
                )

        # 检查 DOI 格式
        if 'doi' in entry:
            doi = entry['doi']
            if not re.match(r'^(10\.\d{4,}/|https://doi.org/10\.)', doi):
                issues.append(
                    f"  [{entry['ID']}] Invalid DOI format: {doi}"
                )

    return issues

def normalize_author_names(entries):
    """标准化作者名格式：Last, First M."""
    for entry in entries:
        if 'author' in entry:
            authors = entry['author'].split(' and ')
            normalized = []
            for author in authors:
                author = author.strip()
                if ',' not in author:
                    parts = author.split()
                    if len(parts) >= 2:
                        author = f"{parts[-1]}, {' '.join(parts[:-1])}"
                normalized.append(author)
            entry['author'] = ' and '.join(normalized)
    return entries

def convert_to_format(entries, target_format):
    """转换引用格式（修改 field 值）"""
    for entry in entries:
        if target_format == 'ieee':
            # IEEE 使用缩写的期刊名（需要映射表）
            # IEEE 使用 month 缩写
            pass
        elif target_format == 'apa':
            # APA 使用 sentence case 的标题
            if 'title' in entry:
                title = entry['title']
                if title[0].isupper() and title[1:].isupper():
                    entry['title'] = title.capitalize()
        elif target_format == 'gbt7714':
            # GB/T 7714 作者名大写
            if 'author' in entry:
                entry['author'] = entry['author'].upper()
    return entries
```

### 引用验证清单

```markdown
## Citation Verification Checklist

### 格式一致性
- [ ] 全文使用同一种引用风格
- [ ] 引用编号连续（数字风格）或字母排序（作者年份风格）
- [ ] 文内引用格式与参考文献列表一致
- [ ] 所有引用的文献都在参考文献列表中
- [ ] 参考文献列表中的每篇都被文内引用

### 内容准确性
- [ ] 作者名拼写正确
- [ ] 标题完整且大小写正确
- [ ] 年份准确
- [ ] 期刊/会议名称正确（缩写或全称，按要求）
- [ ] 卷号、期号、页码正确
- [ ] DOI 有效且可访问

### BibTeX 检查
- [ ] Citation key 命名规范
- [ ] 所有必填字段完整
- [ ] 特殊字符正确转义（& → \&, # → \#）
- [ ] 连字符使用 --（en-dash）而非 -（hyphen）
- [ ] 数学符号使用 LaTeX 格式

### 最终检查
- [ ] 无重复条目
- [ ] 无空白/占位条目
- [ ] 编译无 warning
- [ ] 最终 PDF 中引用显示正确
```

#### 常见 BibTeX 错误

```markdown
## BibTeX 常见错误

### 特殊字符
❌ title = {AT&T's Network}          → & 是特殊字符
✅ title = {AT{\&}T's Network}

❌ title = {Results #1}              → # 是特殊字符
✅ title = {Results {\#}1}

❌ title = {Cost: $100}              → $ 是特殊字符
✅ title = {Cost: {\$}100}

❌ title = {50% improvement}         → % 是特殊字符
✅ title = {50{\%} improvement}

### 数字范围
❌ pages = {123-145}                 → 连字符
✅ pages = {123--145}                → en-dash

### 大小写保护
❌ title = {BERT: Pre-training of Deep Bidirectional Transformers}
   → BibTeX 可能将 BERT 转为 Bert
✅ title = {{BERT}: Pre-training of Deep Bidirectional Transformers}
   → {} 保护大小写
```

### LaTeX 引用宏包对比

```markdown
## LaTeX 引用宏包选择

### natbib（传统方案）
```latex
\usepackage{natbib}
\bibliographystyle{plainnat}  % 或 abbrvnat, unsrtnat
\citet{smith2024}    → Smith et al. (2024)
\citep{smith2024}    → (Smith et al., 2024)
\citeauthor{smith2024} → Smith et al.
\citeyear{smith2024} → 2024
```

### biblatex（现代方案，推荐）
```latex
\usepackage[backend=biber, style=ieee]{biblatex}
\addbibresource{references.bib}
\cite{smith2024}           → [1] (IEEE) 或 Smith et al. (2024) (APA)
\parencite{smith2024}      → [1] 或 (Smith et al., 2024)
\textcite{smith2024}       → Smith et al. [1] 或 Smith et al. (2024)
\autocite{smith2024}       → 自动选择合适的格式
\printbibliography          → 输出参考文献列表
```

### gbt7714（GB/T 7714 中文标准）
```latex
\usepackage[super,sort&compress]{gbt7714}
\bibliographystyle{gbt7714-numerical}
\cite{smith2024}    → [1]
```
```

## Templates

### BibTeX 条目快速生成模板

```bibtex
% 期刊论文
@article{key, author={}, title={}, journal={}, year={}, volume={}, number={}, pages={}, doi={}}

% 会议论文
@inproceedings{key, author={}, title={}, booktitle={}, year={}, pages={}, address={}, publisher={}}

% arXiv 预印本
@article{key, author={}, title={}, journal={arXiv preprint arXiv:XXXX.XXXXX}, year={}, eprint={}, archiveprefix={arXiv}, primaryclass={cs.XX}}
```

### 引用格式转换检查脚本模板

```python
import re

def check_bib_format(bib_path, style='ieee'):
    """检查 .bib 文件格式问题"""
    with open(bib_path) as f:
        content = f.read()
    issues = []
    if re.search(r'pages\s*=\s*"\d+-\d+"', content):
        issues.append("Use -- (en-dash) instead of - (hyphen) in pages")
    if re.search(r'title\s*=\s*"[^{].*BERT[^}]"', content):
        issues.append("Protect acronyms in title with braces: {BERT}")
    return issues
```

### 引用审计报告模板

```markdown
## Citation Audit Report
- Total entries: XX
- Missing DOI: XX
- Missing pages: XX
- Duplicate keys: XX
- Inconsistent author format: XX
- Action items: [ ] Fix duplicates  [ ] Add DOIs  [ ] Normalize names
```

## Common Patterns

### 引用工作流

```
1. 确认目标期刊/会议 → 获取引用格式要求
2. 在 Zotero 中配置 → 设置 citation key 和导出格式
3. 写作中引用 → \cite{} 或 \parencite{}
4. 编译检查 → bibtex/biber + pdflatex
5. 最终验证 → 格式一致性 + 内容准确性
```

## Pitfalls to Avoid

1. **混合引用风格**：同一论文中混用 APA 和 IEEE 格式
2. **只检查编译不检查内容**：编译通过不代表内容正确
3. **忽略期刊特殊要求**：有些期刊有额外的引用格式要求
4. **手动编辑 .bbl 文件**：每次编译会覆盖，应编辑 .bib 文件
5. **引用截断**：长标题或作者列表可能被意外截断
6. **URL 换行**：长 URL 在 PDF 中可能溢出，使用 url 宏包
7. **中英文混排**：注意 GB/T 7714 中英文作者名的处理差异

## Resources

- [APA Style 7th Edition](https://apastyle.apa.org/)
- [IEEE Reference Guide](https://ieeeauthorcenter.ieee.org/create-your-ieee-article/create-ieee-reference/)
- [Chicago Manual of Style](https://www.chicagomanualofstyle.org/)
- [GB/T 7714-2015 全文](https://std.samr.gov.cn/gb/search/gbDetailed?id=71F772D8055ED3A7E05397BE0A0AB82A)
- [gbt7714 LaTeX 宏包](https://github.com/zepinglee/gbt7714-bibtex-style)
- [Citation Style Language (CSL)](https://citationstyles.org/)
