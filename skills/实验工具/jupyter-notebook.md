# Jupyter Notebook 最佳实践

> Category: 实验工具 | Difficulty: beginner | Last updated: 2026

## When to Use

当用户需要创建、组织或优化 Jupyter Notebook 时使用此技能。适用于数据分析、机器学习实验、教学材料、研究演示等场景。当用户提及 Jupyter Notebook、JupyterLab、.ipynb 文件、notebook 组织、notebook 模板、代码可复现性 或 notebook 版本控制 时触发。

## Instructions for AI Assistant

### 基本原则

1. **可读性**：Notebook 首先是文档，然后是代码
2. **线性执行**：从上到下执行应无错误
3. **模块化**：一个 Notebook 只解决一个主要问题
4. **版本控制**：配合 nbstripout 清理输出后提交
5. **可复现**：固定随机种子，记录环境依赖

### Notebook 结构模板

```markdown
## 标准 Notebook 结构

1. **标题和元数据** (Markdown)
   - 项目标题、作者、日期
   - 版本信息、许可证

2. **目录** (Markdown)
   - 自动生成的 TOC

3. **环境设置** (Code)
   - 导入库
   - 配置常量
   - 设置随机种子

4. **数据加载** (Code)
   - 数据源路径
   - 数据读取和初步检查

5. **数据探索 (EDA)** (Code + Markdown)
   - 描述统计
   - 可视化
   - 数据质量检查

6. **数据预处理** (Code)
   - 清洗、转换、特征工程

7. **模型/分析** (Code + Markdown)
   - 核心逻辑
   - 中间结果解释

8. **结果评估** (Code + Markdown)
   - 指标计算
   - 可视化

9. **结论** (Markdown)
   - 主要发现
   - 后续步骤

10. **附录** (Code)
    - 辅助函数
    - 额外实验
```

### 完整 Notebook 模板

```python
# %% [markdown]
# # 项目标题：[具体分析/实验名称]
#
# **作者**: [Your Name]
# **日期**: [YYYY-MM-DD]
# **版本**: [v1.0]
#
# ## 目标
# [简述本 Notebook 的目的和预期输出]
#
# ## 数据
# - 来源: [数据集名称/URL]
# - 大小: [行数 x 列数]
# - 格式: [CSV/Parquet/etc.]

# %% [markdown]
# ## 1. 环境设置

# %%
import sys
import warnings
from pathlib import Path

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# 配置
warnings.filterwarnings('ignore')
np.random.seed(42)
pd.set_option('display.max_columns', 50)
pd.set_option('display.float_format', '{:.4f}'.format)

# 项目路径
PROJECT_ROOT = Path('.').resolve()
DATA_DIR = PROJECT_ROOT / 'data'
OUTPUT_DIR = PROJECT_ROOT / 'output'
OUTPUT_DIR.mkdir(exist_ok=True)

# 图表样式
sns.set_theme(style="ticks", font_scale=1.1)
plt.rcParams['figure.dpi'] = 100

print(f"Python: {sys.version}")
print(f"NumPy: {np.__version__}")
print(f"Pandas: {pd.__version__}")

# %% [markdown]
# ## 2. 数据加载

# %%
# 加载数据
df = pd.read_csv(DATA_DIR / 'dataset.csv')

# 基本信息
print(f"数据形状: {df.shape}")
print(f"\n数据类型:\n{df.dtypes}")
print(f"\n前5行:")
df.head()

# %% [markdown]
# ## 3. 探索性数据分析 (EDA)

# %%
# 描述统计
df.describe()

# %%
# 缺失值检查
missing = df.isnull().sum()
missing_pct = (missing / len(df) * 100).round(2)
missing_df = pd.DataFrame({'count': missing, 'pct': missing_pct})
print(missing_df[missing_df['count'] > 0])

# %%
# 分布可视化
fig, axes = plt.subplots(2, 3, figsize=(12, 8))
for i, col in enumerate(df.select_dtypes(include=[np.number]).columns[:6]):
    ax = axes[i // 3, i % 3]
    df[col].hist(ax=ax, bins=30, edgecolor='black', linewidth=0.5)
    ax.set_title(col)
plt.tight_layout()
plt.savefig(OUTPUT_DIR / 'distributions.png', dpi=150, bbox_inches='tight')
plt.show()

# %% [markdown]
# ## 4. 数据预处理

# %%
# 数据清洗
df_clean = df.dropna(subset=['target_column'])
df_clean = df_clean[df_clean['value'] > 0]

# 特征工程
df_clean['feature_new'] = df_clean['col_a'] / (df_clean['col_b'] + 1e-8)

print(f"清洗后数据形状: {df_clean.shape}")

# %% [markdown]
# ## 5. 模型 / 分析

# %%
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import classification_report, confusion_matrix

# 数据划分
X = df_clean.drop('target', axis=1)
y = df_clean['target']
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42, stratify=y
)

# 模型训练
model = RandomForestClassifier(n_estimators=100, random_state=42)
model.fit(X_train, y_train)

# 预测
y_pred = model.predict(X_test)

# %% [markdown]
# ## 6. 结果评估

# %%
# 分类报告
print(classification_report(y_test, y_pred))

# 混淆矩阵
fig, ax = plt.subplots(figsize=(6, 5))
sns.heatmap(confusion_matrix(y_test, y_pred), annot=True, fmt='d',
            cmap='Blues', ax=ax)
ax.set_xlabel('Predicted')
ax.set_ylabel('Actual')
ax.set_title('Confusion Matrix')
plt.tight_layout()
plt.savefig(OUTPUT_DIR / 'confusion_matrix.png', dpi=150, bbox_inches='tight')
plt.show()

# 特征重要性
importances = pd.Series(model.feature_importances_, index=X.columns)
importances.nlargest(10).plot(kind='barh')
plt.title('Top 10 Feature Importances')
plt.tight_layout()
plt.savefig(OUTPUT_DIR / 'feature_importance.png', dpi=150, bbox_inches='tight')
plt.show()

# %% [markdown]
# ## 7. 结论
#
# ### 主要发现
# 1. [发现1]
# 2. [发现2]
# 3. [发现3]
#
# ### 后续工作
# - [待做1]
# - [待做2]

# %% [markdown]
# ## 附录：环境信息

# %%
# 导出环境依赖
!pip freeze > requirements.txt

# 记录运行时间
import datetime
print(f"Notebook 运行完成: {datetime.datetime.now()}")
```

### Markdown Cell 格式化

```markdown
## Markdown 格式指南

### 标题层级
# 一级标题 (Notebook 标题)
## 二级标题 (主要章节)
### 三级标题 (子章节)
#### 四级标题 (段落标题)

### 列表
- 无序列表项1
- 无序列表项2
  - 嵌套项

1. 有序列表项1
2. 有序列表项2

### 数学公式
行内: $E = mc^2$
行间:
$$\frac{\partial L}{\partial \theta} = \frac{1}{N} \sum_{i=1}^{N} \nabla_\theta \ell(f(x_i; \theta), y_i)$$

### 表格
| 指标 | 值 | 说明 |
|------|-----|------|
| Accuracy | 95.3% | 正确分类比例 |
| F1 Score | 0.94 | 精确率和召回率的调和平均 |

### 代码引用
使用 `model.fit()` 训练模型。

### 警告和提示
> **注意**: 此步骤需要较大内存（>8GB）

> **提示**: 可调整参数 `n_estimators` 优化性能

### 任务列表
- [x] 数据加载
- [x] EDA 完成
- [ ] 模型调优
- [ ] 撰写报告
```

### 代码组织最佳实践

```python
## 代码单元格组织原则

### 1. 一个单元格一个任务
# ✓ 好的做法
# Cell 1: 加载数据
df = pd.read_csv('data.csv')

# Cell 2: 检查缺失值
df.isnull().sum()

# Cell 3: 填充缺失值
df = df.fillna(df.median())

# ✗ 不好的做法（一个单元格做太多事）
df = pd.read_csv('data.csv')
print(df.isnull().sum())
df = df.fillna(df.median())
df['new_col'] = df['a'] + df['b']
df.to_csv('processed.csv')
```

### 2. 辅助函数放在前面

```python
# 在 Notebook 开头定义所有辅助函数
def load_and_validate(path, expected_cols=None):
    """加载数据并验证列名"""
    df = pd.read_csv(path)
    if expected_cols:
        missing = set(expected_cols) - set(df.columns)
        if missing:
            raise ValueError(f"Missing columns: {missing}")
    return df

def plot_learning_curve(train_scores, val_scores, epochs):
    """绘制学习曲线"""
    fig, ax = plt.subplots(figsize=(8, 5))
    ax.plot(epochs, train_scores, label='Train')
    ax.plot(epochs, val_scores, label='Validation')
    ax.set_xlabel('Epoch')
    ax.set_ylabel('Score')
    ax.legend()
    ax.grid(True, alpha=0.3)
    return fig
```

### 3. 输出管理

```python
## 输出管理

### 避免大量输出
# ✓ 限制输出行数
df.head(10)  # 而非直接输出整个 DataFrame

# ✓ 使用 display() 代替 print() 展示 DataFrame
from IPython.display import display, HTML
display(df.describe())

# ✓ 大数据集只显示形状
print(f"Shape: {df.shape}")
print(f"Columns: {list(df.columns)}")

### 清理不需要的输出
# 在提交到版本控制前清理输出
# 方法1: 使用 nbstripout
# pip install nbstripout
# nbstripout notebook.ipynb

# 方法2: JupyterLab 中 Edit → Clear All Outputs

### 魔法命令
%matplotlib inline      # 内嵌显示图表
%load_ext autoreload    # 自动重载模块
%autoreload 2           # 修改 .py 文件后自动重载
%time result = func()   # 计时
%memit result = func()  # 内存使用
```

### 版本控制设置

```markdown
## Jupyter Notebook 版本控制

### 方案1: nbstripout（推荐）

安装:
```bash
pip install nbstripout
nbstripout --install  # 设置 git filter
```

.gitattributes 文件:
```
*.ipynb filter=nbstripout
*.ipynb diff=ipynb
```

### 方案2: Jupytext（双向同步）

安装:
```bash
pip install jupytext
```

将 .ipynb 同步为 .py 或 .md:
```bash
jupytext --to py notebook.ipynb          # 转为 .py
jupytext --to md notebook.ipynb          # 转为 .md
jupytext --set-formats ipynb,py notebook.ipynb  # 双向同步
```

配置 (jupytext.toml):
```toml
formats = "ipynb,py:percent"
```

### 方案3: nbQA（代码质量检查）

```bash
pip install nbqa

# 在 notebook 上运行代码质量工具
nbqa black notebook.ipynb               # 代码格式化
nbqa isort notebook.ipynb               # import 排序
nbqa flake8 notebook.ipynb              # lint 检查
nbqa mypy notebook.ipynb                # 类型检查
```

### 推荐的 .gitignore
```
# Jupyter
.ipynb_checkpoints/
*.ipynb_cells/
__pycache__/
*.py[cod]

# Output
*.png
*.pdf
*.html
*.pkl
*.h5
*.pt
output/
```
```

### 可复现性设置

```python
## 环境可复现性

### requirements.txt 生成
# 方法1: pip freeze
!pip freeze > requirements.txt

# 方法2: pipreqs（只记录实际使用的包）
!pip install pipreqs
!pipreqs . --force --savepath requirements.txt

### environment.yml (conda)
```yaml
name: my-project
channels:
  - defaults
  - conda-forge
dependencies:
  - python=3.11
  - numpy=1.24
  - pandas=2.0
  - scikit-learn=1.3
  - matplotlib=3.7
  - jupyter=1.0
  - pip:
    - some-pip-package==1.0.0
```

### Dockerfile（见 docker-reproducibility skill）
```

### JupyterLab 扩展推荐

```markdown
## 推荐的 JupyterLab 扩展

### 必装
- **jupyterlab-code-formatter**: 代码格式化 (black, isort)
- **jupyterlab-git**: Git 集成
- **jupyterlab-lsp**: 代码智能提示
- **jupyterlab-toc**: 自动生成目录

### 推荐
- **jupyterlab-variable-inspector**: 变量检查器
- **jupyterlab-execute-time**: 显示执行时间
- **jupyterlab-nvdashboard**: GPU 监控
- **jupyterlab-drawio**: 绘图工具

### 安装
```bash
pip install jupyterlab-code-formatter jupyterlab-git
jupyter lab build
```
```

## Templates

### 数据分析快速起步模板

```python
# %% [markdown]
# # 分析标题
# **日期**: YYYY-MM-DD  |  **作者**: Name

# %%
import pandas as pd, numpy as np, matplotlib.pyplot as plt, seaborn as sns
sns.set_theme(style="ticks"); np.random.seed(42)

# %%
df = pd.read_csv("data.csv")
print(f"Shape: {df.shape}"); df.head()
```

### Notebook 项目目录模板

```
notebook-project/
├── notebooks/
│   ├── 01_eda.ipynb
│   ├── 02_preprocessing.ipynb
│   └── 03_modeling.ipynb
├── src/                  # 可复用的 Python 模块
├── data/                 # 原始数据（gitignore）
├── output/               # 结果输出（gitignore）
├── requirements.txt
└── README.md
```

### 环境设置 Cell 模板

```python
# 环境设置 - 每个 Notebook 第一个 Code cell
import sys, warnings; warnings.filterwarnings('ignore')
from pathlib import Path
PROJECT = Path('.').resolve()
DATA = PROJECT / 'data'; OUTPUT = PROJECT / 'output'
OUTPUT.mkdir(exist_ok=True)
print(f"Python {sys.version.split()[0]}")
```

## Common Patterns

### 分析 Notebook 标准流程

```
1. 创建 Notebook → 使用模板
2. 配置环境 → 导入 + 常量 + 种子
3. 加载数据 → 检查形状和类型
4. EDA → 统计 + 可视化
5. 预处理 → 清洗 + 特征工程
6. 建模/分析 → 核心逻辑
7. 评估 → 指标 + 图表
8. 总结 → 结论 + 后续
9. 清理 → nbstripout + 提交
```

### Notebook 转 Python 脚本

```bash
# 使用 jupytext 转换
jupytext --to py:percent notebook.ipynb

# 使用 nbconvert 转换
jupyter nbconvert --to script notebook.ipynb
```

## Pitfalls to Avoid

1. **执行顺序混乱**：多次运行某些单元格导致变量状态不一致
2. **输出过大**：大量输出使 .ipynb 文件过大，拖慢 git
3. **硬编码路径**：使用绝对路径导致在其他机器上无法运行
4. **忽略随机种子**：不设种子导致结果不可复现
5. **一个 Notebook 太长**：超过 200 个单元格应拆分
6. **隐藏状态**：函数依赖于被删除单元格中定义的变量
7. **不记录环境**：缺少 requirements.txt 导致无法复现
8. **二进制文件进 git**：.ipynb 的 JSON 输出占用大量 git 空间

## Resources

- [Jupyter Documentation](https://jupyter.readthedocs.io/)
- [JupyterLab Documentation](https://jupyterlab.readthedocs.io/)
- [nbstripout](https://github.com/kynan/nbstripout)
- [Jupytext](https://jupytext.readthedocs.io/)
- [nbQA](https://nbqa.readthedocs.io/)
- [Effective Jupyter Notebooks - Towards Data Science](https://towardsdatascience.com/)
