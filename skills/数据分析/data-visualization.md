# 数据可视化

> Category: 数据分析 | Difficulty: intermediate | Last updated: 2026

## When to Use

当用户需要创建用于学术论文、研究报告或演示文稿的高质量数据可视化图表时使用此技能。适用于 matplotlib、seaborn、ggplot2、plotly 等工具的使用指导。当用户提及数据可视化、图表制作、publication-quality figure、学术图表、matplotlib/seaborn 配色、图表美化或 figure formatting 时触发。

## Instructions for AI Assistant

### 基本原则

1. **清晰优先**：图表的首要目标是清晰传达信息，美观次之
2. **适合数据类型**：根据数据特征选择合适的图表类型
3. **无障碍设计**：考虑色盲友好、黑白打印可辨识
4. **出版标准**：满足期刊的图片分辨率、尺寸和格式要求
5. **可复现性**：代码化所有图表，避免手动调整

### 图表类型选择指南

```
┌───────────────────────────────────────────────────────────────┐
│                    图表类型选择决策树                          │
├───────────────────────────────────────────────────────────────┤
│                                                               │
│  比较 ──┬── 少量类别(≤7) ──→ 柱状图 (bar chart)              │
│         ├── 多类别         ──→ 水平柱状图 / 雷达图           │
│         └── 时间序列       ──→ 折线图 (line chart)            │
│                                                               │
│  分布 ──┬── 单变量         ──→ 直方图 / KDE / 箱线图          │
│         ├── 多组比较       ──→ 小提琴图 / 箱线图 + strip      │
│         └── 二维分布       ──→ 散点密度图 / hexbin            │
│                                                               │
│  关系 ──┬── 两变量         ──→ 散点图 (scatter)              │
│         ├── 多变量         ──→ 矩阵散点图 / 热力图           │
│         └── 网络/层次      ──→ 树状图 / 桑基图               │
│                                                               │
│  组成 ──┬── 静态           ──→ 饼图(少类) / 堆叠柱状图       │
│         └── 随时间变化     ──→ 堆叠面积图 / 河流图            │
│                                                               │
└───────────────────────────────────────────────────────────────┘
```

### 出版级图表通用设置

```python
import matplotlib.pyplot as plt
import matplotlib as mpl
import numpy as np

def set_publication_style():
    """设置出版级 matplotlib 样式"""
    mpl.rcParams.update({
        # 字体
        'font.family': 'serif',
        'font.serif': ['Times New Roman', 'DejaVu Serif'],
        'font.size': 10,
        'mathtext.fontset': 'dejavuserif',

        # 坐标轴
        'axes.labelsize': 11,
        'axes.titlesize': 12,
        'axes.linewidth': 0.8,
        'axes.spines.top': False,
        'axes.spines.right': False,

        # 刻度
        'xtick.labelsize': 9,
        'ytick.labelsize': 9,
        'xtick.direction': 'in',
        'ytick.direction': 'in',
        'xtick.major.size': 4,
        'ytick.major.size': 4,
        'xtick.major.width': 0.8,
        'ytick.major.width': 0.8,

        # 图例
        'legend.fontsize': 9,
        'legend.frameon': False,
        'legend.borderpad': 0.3,

        # 图片分辨率
        'savefig.dpi': 300,
        'savefig.bbox': 'tight',
        'savefig.pad_inches': 0.05,

        # 线条
        'lines.linewidth': 1.5,
        'lines.markersize': 5,
    })

# 单列 / 双列尺寸 (inches)
SINGLE_COL = (3.5, 2.8)    # 单栏宽度 ~89mm
DOUBLE_COL = (7.2, 4.5)    # 双栏宽度 ~183mm
HALF_COL = (5.0, 3.5)      # 1.5栏宽度 ~127mm
```

### 出版级配色方案

```python
# 学术论文推荐配色方案

# 方案1：色盲友好 (Paul Tol's Bright)
TOL_BRIGHT = ['#4477AA', '#EE6677', '#228833', '#CCBB44',
              '#66CCEE', '#AA3377', '#BBBBBB']

# 方案2：Nature 风格
NATURE_COLORS = ['#E64B35', '#4DBBD5', '#00A087', '#3C5488',
                 '#F39B7F', '#8491B4', '#91D1C2']

# 方案3：Science 风格
SCIENCE_COLORS = ['#3B4992', '#EE0000', '#008B45', '#631879',
                  '#008280', '#BB0021', '#5F559B']

# 方案4：适用于黑白打印
BW_FRIENDLY = ['#000000', '#666666', '#999999', '#CCCCCC',
               '#000000', '#666666', '#999999']
BW_STYLES = ['-', '--', '-.', ':', '-', '--', '-.']

# 方案5：Seaborn 学术风格
import seaborn as sns
sns.set_palette("colorblind")  # 色盲友好

def apply_colorblind_palette():
    """应用色盲友好配色"""
    sns.set_palette("colorblind")
    return sns.color_palette("colorblind", 8)

# Colorblind-safe 检测工具
def test_palette_visibility(colors):
    """测试配色在色盲模拟下的可区分性"""
    try:
        from colorspacious import cspace_convert
        for cb_type in ['deuteranomaly', 'protanomaly', 'tritanomaly']:
            print(f"\n{cb_type} simulation:")
            for i, c in enumerate(colors):
                rgb = mpl.colors.to_rgb(c)
                lab = cspace_convert(rgb, 'sRGB1', 'CIELab')
                print(f"  Color {i}: L*={lab[0]:.1f} a*={lab[1]:.1f} b*={lab[2]:.1f}")
    except ImportError:
        print("Install colorspacious for colorblind simulation")
```

### 常用图表模板

#### 1. 柱状图 + 误差线

```python
def bar_chart_with_error(data, labels, errors, ylabel, title=None,
                         colors=None, figsize=SINGLE_COL):
    """出版级柱状图"""
    set_publication_style()
    fig, ax = plt.subplots(figsize=figsize)

    x = np.arange(len(labels))
    width = 0.6

    if colors is None:
        colors = TOL_BRIGHT[:len(labels)]

    bars = ax.bar(x, data, width, yerr=errors, capsize=4,
                  color=colors, edgecolor='black', linewidth=0.5,
                  error_kw={'linewidth': 0.8})

    ax.set_xlabel('Method')
    ax.set_ylabel(ylabel)
    ax.set_xticks(x)
    ax.set_xticklabels(labels, rotation=30, ha='right')
    ax.set_ylim(bottom=0)

    if title:
        ax.set_title(title)

    # 添加数值标签
    for bar, val in zip(bars, data):
        ax.text(bar.get_x() + bar.get_width()/2, bar.get_height() + 0.01,
                f'{val:.2f}', ha='center', va='bottom', fontsize=8)

    plt.tight_layout()
    return fig, ax
```

#### 2. 折线图（学习曲线）

```python
def learning_curves(epochs, train_values, val_values, metrics,
                    xlabel='Epoch', ylabel='Loss', figsize=SINGLE_COL):
    """学习曲线图"""
    set_publication_style()
    fig, ax = plt.subplots(figsize=figsize)

    styles = ['-', '--', '-.', ':']

    for i, (train, val, label) in enumerate(
            zip(train_values, val_values, metrics)):
        ax.plot(epochs, train, styles[i % 4], color=TOL_BRIGHT[i],
                label=f'{label} (train)', linewidth=1.5)
        ax.plot(epochs, val, styles[i % 4], color=TOL_BRIGHT[i],
                marker='o', markersize=3, markevery=5,
                label=f'{label} (val)', linewidth=1.5, alpha=0.7)

    ax.set_xlabel(xlabel)
    ax.set_ylabel(ylabel)
    ax.legend(loc='best', ncol=1)
    ax.grid(True, alpha=0.3, linewidth=0.5)

    plt.tight_layout()
    return fig, ax
```

#### 3. 箱线图 + 散点

```python
def boxplot_with_strip(data_groups, labels, ylabel,
                       figsize=SINGLE_COL):
    """箱线图叠加散点，展示数据分布"""
    set_publication_style()
    fig, ax = plt.subplots(figsize=figsize)

    positions = range(1, len(data_groups) + 1)

    # 箱线图
    bp = ax.boxplot(data_groups, positions=positions, widths=0.5,
                    patch_artist=True, showfliers=False,
                    boxprops=dict(linewidth=0.8),
                    whiskerprops=dict(linewidth=0.8),
                    medianprops=dict(color='black', linewidth=1.2))

    for patch, color in zip(bp['boxes'], TOL_BRIGHT):
        patch.set_facecolor(color)
        patch.set_alpha(0.6)

    # 叠加散点（带抖动）
    for i, group in enumerate(data_groups):
        jitter = np.random.normal(0, 0.04, size=len(group))
        ax.scatter(np.full_like(group, positions[i]) + jitter, group,
                   alpha=0.5, s=15, color=TOL_BRIGHT[i],
                   edgecolor='black', linewidth=0.3)

    ax.set_xticks(list(positions))
    ax.set_xticklabels(labels)
    ax.set_ylabel(ylabel)

    plt.tight_layout()
    return fig, ax
```

#### 4. 热力图（混淆矩阵 / 相关矩阵）

```python
def heatmap(matrix, xlabels, ylabels, title=None, cmap='RdYlBu_r',
            figsize=(4, 3.5), fmt='.2f', annotate=True):
    """热力图（混淆矩阵或相关矩阵）"""
    set_publication_style()
    fig, ax = plt.subplots(figsize=figsize)

    im = ax.imshow(matrix, cmap=cmap, aspect='auto')

    if annotate:
        for i in range(len(ylabels)):
            for j in range(len(xlabels)):
                val = matrix[i, j]
                text_color = 'white' if abs(val - matrix.mean()) > matrix.std() else 'black'
                ax.text(j, i, f'{val:{fmt}}', ha='center', va='center',
                        fontsize=8, color=text_color)

    ax.set_xticks(range(len(xlabels)))
    ax.set_yticks(range(len(ylabels)))
    ax.set_xticklabels(xlabels, rotation=45, ha='right')
    ax.set_yticklabels(ylabels)

    cbar = plt.colorbar(im, ax=ax, shrink=0.8)
    cbar.ax.tick_params(labelsize=8)

    if title:
        ax.set_title(title, fontsize=11, pad=10)

    plt.tight_layout()
    return fig, ax
```

#### 5. 多子图布局

```python
def multi_panel_figure(n_panels, ncols=2, figsize=None):
    """多子图统一布局"""
    nrows = (n_panels + ncols - 1) // ncols
    if figsize is None:
        figsize = (DOUBLE_COL[0], DOUBLE_COL[1] * nrows / 2)

    fig, axes = plt.subplots(nrows, ncols, figsize=figsize)

    if n_panels == 1:
        axes = np.array([axes])
    axes = axes.flatten()

    # 隐藏多余的子图
    for i in range(n_panels, len(axes)):
        axes[i].set_visible(False)

    # 添加子图标签 (a), (b), (c)...
    for i, ax in enumerate(axes[:n_panels]):
        ax.text(-0.1, 1.05, f'({chr(97+i)})', transform=ax.transAxes,
                fontsize=12, fontweight='bold', va='top')

    return fig, axes
```

#### 6. 散点图 + 回归线

```python
def scatter_with_regression(x, y, xlabel, ylabel, figsize=SINGLE_COL,
                            show_ci=True, group_labels=None):
    """散点图 + 回归线 + 置信区间"""
    set_publication_style()
    fig, ax = plt.subplots(figsize=figsize)

    if group_labels is None:
        ax.scatter(x, y, alpha=0.6, s=25, color=TOL_BRIGHT[0],
                   edgecolor='black', linewidth=0.3)

        # 回归线
        z = np.polyfit(x, y, 1)
        p = np.poly1d(z)
        x_line = np.linspace(min(x), max(x), 100)
        ax.plot(x_line, p(x_line), '--', color='black', linewidth=1)

        # 置信区间
        if show_ci:
            from scipy import stats as sp_stats
            slope, intercept, r, p_val, se = sp_stats.linregress(x, y)
            y_pred = slope * x_line + intercept
            n = len(x)
            t_val = sp_stats.t.ppf(0.975, n - 2)
            se_line = se * np.sqrt(1/n + (x_line - np.mean(x))**2 /
                                    np.sum((x - np.mean(x))**2))
            ax.fill_between(x_line, y_pred - t_val * se_line,
                            y_pred + t_val * se_line,
                            alpha=0.15, color=TOL_BRIGHT[0])

    ax.set_xlabel(xlabel)
    ax.set_ylabel(ylabel)

    plt.tight_layout()
    return fig, ax
```

### 图片尺寸和分辨率规范

```markdown
## 期刊图片规格

| 期刊/会议 | 单栏宽度 | 双栏宽度 | 分辨率 | 格式 |
|-----------|---------|---------|--------|------|
| IEEE      | 3.5 in (89mm) | 7.2 in (183mm) | ≥300 dpi | EPS/PDF/TIFF |
| ACM       | 3.3 in (86mm) | 6.8 in (173mm) | ≥300 dpi | EPS/PDF/PNG |
| Elsevier  | 90mm    | 190mm   | ≥300 dpi | EPS/PDF/TIFF |
| Springer  | 84mm    | 174mm   | ≥300 dpi | EPS/PDF/TIFF |
| Nature    | 89mm    | 183mm   | ≥300 dpi | EPS/PDF/TIFF |
| Science   | 57mm    | 120mm   | ≥300 dpi | EPS/PDF/TIFF |

## 导出设置

```python
# 导出高质量图片
fig.savefig('figure1.pdf', dpi=300, bbox_inches='tight',
            pad_inches=0.05, transparent=False)
fig.savefig('figure1.eps', dpi=300, bbox_inches='tight')
fig.savefig('figure1.png', dpi=600, bbox_inches='tight')  # PNG 用更高分辨率
```
```

### Seaborn 学术风格模板

```python
import seaborn as sns
import pandas as pd

def seaborn_setup():
    """Seaborn 学术风格初始化"""
    sns.set_theme(style="ticks", font_scale=1.1)
    sns.set_palette("colorblind")
    plt.rcParams.update({
        'font.family': 'serif',
        'font.serif': ['Times New Roman'],
        'axes.linewidth': 0.8,
        'xtick.major.width': 0.8,
        'ytick.major.width': 0.8,
    })

def seaborn_grouped_bar(df, x, y, hue, xlabel, ylabel, figsize=SINGLE_COL):
    """分组柱状图"""
    seaborn_setup()
    fig, ax = plt.subplots(figsize=figsize)
    sns.barplot(data=df, x=x, y=y, hue=hue, ax=ax,
                edgecolor='black', linewidth=0.5, capsize=0.1)
    ax.set_xlabel(xlabel)
    ax.set_ylabel(ylabel)
    ax.legend(title=hue, frameon=False)
    sns.despine()
    plt.tight_layout()
    return fig, ax

def seaborn_violin(df, x, y, xlabel, ylabel, figsize=SINGLE_COL):
    """小提琴图 + strip plot"""
    seaborn_setup()
    fig, ax = plt.subplots(figsize=figsize)
    sns.violinplot(data=df, x=x, y=y, ax=ax, inner=None,
                   linewidth=0.8, alpha=0.6)
    sns.stripplot(data=df, x=x, y=y, ax=ax, size=3,
                  alpha=0.5, jitter=0.15, color='black')
    ax.set_xlabel(xlabel)
    ax.set_ylabel(ylabel)
    sns.despine()
    plt.tight_layout()
    return fig, ax

def seaborn_regression(df, x, y, hue=None, figsize=DOUBLE_COL):
    """回归散点图"""
    seaborn_setup()
    g = sns.lmplot(data=df, x=x, y=y, hue=hue,
                   height=figsize[1], aspect=figsize[0]/figsize[1],
                   scatter_kws={'s': 20, 'alpha': 0.5},
                   line_kws={'linewidth': 1.5})
    return g
```

### ggplot2 (R) 模板

```r
library(ggplot2)
library(ggpubr)
library(RColorBrewer)

# 出版级主题
theme_publication <- function(base_size = 10) {
  theme_bw(base_size = base_size) +
    theme(
      text = element_text(family = "serif"),
      axis.title = element_text(size = base_size + 1),
      axis.text = element_text(size = base_size - 1, color = "black"),
      axis.line = element_line(linewidth = 0.5),
      axis.ticks = element_line(linewidth = 0.5),
      panel.border = element_blank(),
      panel.grid.major = element_blank(),
      panel.grid.minor = element_blank(),
      legend.position = "bottom",
      legend.key.size = unit(0.8, "lines"),
      legend.background = element_blank()
    )
}

# 柱状图
ggplot(data, aes(x = method, y = accuracy, fill = method)) +
  geom_bar(stat = "identity", width = 0.6, color = "black", linewidth = 0.3) +
  geom_errorbar(aes(ymin = accuracy - sd, ymax = accuracy + sd),
                width = 0.2, linewidth = 0.5) +
  scale_fill_brewer(palette = "Set2") +
  labs(x = "Method", y = "Accuracy (%)") +
  theme_publication()

# 箱线图 + 散点
ggplot(data, aes(x = group, y = value, fill = group)) +
  geom_boxplot(width = 0.5, outlier.shape = NA, alpha = 0.6) +
  geom_jitter(width = 0.15, size = 1.5, alpha = 0.5) +
  scale_fill_brewer(palette = "Set2") +
  labs(x = "Group", y = "Score") +
  theme_publication()

# 保存
ggsave("figure1.pdf", width = 89, height = 70, units = "mm", dpi = 300)
```

## Templates

### 出版级柱状图快速模板

```python
import matplotlib.pyplot as plt
import numpy as np

def pub_bar(labels, values, errors, ylabel, save_path=None):
    """3行代码生成出版级柱状图"""
    fig, ax = plt.subplots(figsize=(3.5, 2.8))
    ax.bar(range(len(labels)), values, yerr=errors, capsize=4,
           color=['#4477AA','#EE6677','#228833','#CCBB44'], edgecolor='black', linewidth=0.5)
    ax.set_xticks(range(len(labels))); ax.set_xticklabels(labels)
    ax.set_ylabel(ylabel); ax.spines[['top','right']].set_visible(False)
    if save_path: fig.savefig(save_path, dpi=300, bbox_inches='tight')
```

### 多子图对比布局模板

```python
fig, axes = plt.subplots(1, 3, figsize=(7.2, 2.8))
for i, (ax, title) in enumerate(zip(axes, ['(a)', '(b)', '(c)'])):
    ax.text(-0.1, 1.05, title, transform=ax.transAxes, fontsize=12, fontweight='bold')
    ax.spines[['top','right']].set_visible(False)
plt.tight_layout()
```

### 快速保存多格式模板

```python
def save_figure(fig, name):
    """同时保存 PDF、EPS 和高分辨率 PNG"""
    for fmt, dpi in [('pdf',300), ('eps',300), ('png',600)]:
        fig.savefig(f'{name}.{fmt}', dpi=dpi, bbox_inches='tight', pad_inches=0.05)
```

## Common Patterns

### 图表检查清单

```markdown
## Figure Quality Checklist

### 基础要求
- [ ] 图片尺寸符合期刊要求
- [ ] 分辨率 ≥ 300 dpi（位图）
- [ ] 使用矢量格式（PDF/EPS/SVG）
- [ ] 字体大小可读（≥ 8pt after scaling）

### 内容完整
- [ ] 坐标轴标签清晰（含单位）
- [ ] 图例说明清楚
- [ ] 误差线/置信区间标注
- [ ] 统计显著性标注（如适用）

### 无障碍设计
- [ ] 色盲友好配色
- [ ] 黑白打印可区分（线型+标记区分）
- [ ] 线条粗细足够（≥ 1pt）
- [ ] 标记大小足够（≥ 4pt）

### 一致性
- [ ] 多图间配色方案一致
- [ ] 字体和大小一致
- [ ] 缩写和术语一致
```

## Pitfalls to Avoid

1. **3D 图表**：除非必要，避免 3D 效果，它会扭曲数据感知
2. **双 Y 轴**：容易造成误导，优先使用子图或标准化
3. **饼图过度使用**：超过 5 个类别时改用柱状图
4. **彩虹配色**：jet/rainbow colormap 有感知不均匀问题，使用 viridis/cividis
5. **截断 Y 轴**：柱状图不从 0 开始会误导读者
6. **过多装饰**：避免阴影、渐变、过多网格线等装饰性元素
7. **忽略数据点**：在柱状图/箱线图上叠加散点，展示实际数据分布
8. **字号过小**：打印后文字应 ≥ 8pt，确保可读性
9. **不一致的配色**：同一论文中相同类别的颜色应保持一致

## Resources

- [matplotlib Documentation](https://matplotlib.org/)
- [seaborn Tutorial](https://seaborn.pydata.org/tutorial.html)
- [ggplot2 Documentation](https://ggplot2.tidyverse.org/)
- [Color Brewer 2.0](https://colorbrewer2.org/) - 配色方案选择器
- [Paul Tol's Colour Schemes](https://personal.sron.nl/~pault/) - 科研配色
- [Scientific Figure Design Guide - PLOS](https://journals.plos.org/ploscompbiol/s/figures)
- [Fundamentals of Data Visualization - Claus Wilke](https://clauswilke.com/dataviz/)
