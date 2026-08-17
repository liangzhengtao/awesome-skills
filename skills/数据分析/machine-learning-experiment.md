# 机器学习实验管理

> Category: 数据分析 | Difficulty: advanced | Last updated: 2026

## When to Use

当用户需要设计、执行、追踪或报告机器学习实验时使用此技能。适用于模型训练、超参数调优、实验记录、结果对比和论文实验章节撰写。当用户提及 ML experiment、实验管理、hyperparameter tuning、实验追踪、experiment tracking、模型训练、cross-validation、结果复现 或 reproducibility 时触发。

## Instructions for AI Assistant

### 基本原则

1. **可复现性**：所有实验必须可精确复现
2. **系统化**：实验应有结构化的管理方式
3. **高效性**：善用自动化工具减少手动操作
4. **完整性**：记录所有影响结果的因素
5. **可比较性**：确保对比实验的公平性

### 实验追踪设置

#### Weights & Biases (W&B)

```python
import wandb

def setup_wandb(project_name, experiment_name, config=None):
    """初始化 W&B 实验追踪"""
    run = wandb.init(
        project=project_name,
        name=experiment_name,
        config=config or {},
        tags=["baseline", "v1"],
        notes="Initial experiment with baseline model",
        save_code=True,  # 保存代码快照
    )
    return run

# 使用示例
config = {
    "architecture": "resnet50",
    "learning_rate": 1e-3,
    "batch_size": 32,
    "epochs": 100,
    "optimizer": "adam",
    "weight_decay": 1e-4,
    "scheduler": "cosine",
    "seed": 42,
}

run = setup_wandb("my-project", "exp-001-baseline", config)

# 训练循环中记录指标
for epoch in range(config["epochs"]):
    train_loss, train_acc = train_one_epoch(model, train_loader)
    val_loss, val_acc = evaluate(model, val_loader)

    wandb.log({
        "epoch": epoch,
        "train/loss": train_loss,
        "train/accuracy": train_acc,
        "val/loss": val_loss,
        "val/accuracy": val_acc,
        "learning_rate": scheduler.get_last_lr()[0],
    })

    # 记录图表
    wandb.log({"confusion_matrix": wandb.plot.confusion_matrix(
        y_true=labels, preds=predictions, class_names=class_names
    )})

run.finish()
```

#### MLflow

```python
import mlflow
import mlflow.pytorch

def setup_mlflow(experiment_name):
    """初始化 MLflow"""
    mlflow.set_experiment(experiment_name)

def log_experiment(params, metrics, model=None, artifacts=None):
    """记录一次实验"""
    with mlflow.start_run(run_name=params.get("run_name", "default")):
        # 记录参数
        mlflow.log_params(params)

        # 记录指标
        for key, value in metrics.items():
            mlflow.log_metric(key, value)

        # 记录模型
        if model is not None:
            mlflow.pytorch.log_model(model, "model")

        # 记录文件
        if artifacts:
            for artifact_path in artifacts:
                mlflow.log_artifact(artifact_path)

        # 记录代码
        mlflow.log_artifact("train.py")

# 使用示例
params = {
    "run_name": "resnet50-baseline",
    "architecture": "resnet50",
    "learning_rate": 1e-3,
    "batch_size": 32,
    "epochs": 100,
    "seed": 42,
}

metrics = {
    "final_train_loss": 0.12,
    "final_val_loss": 0.25,
    "best_val_accuracy": 94.5,
    "training_time_hours": 2.3,
}

log_experiment(params, metrics, model=model)
```

#### 纯 Python 最小追踪方案

```python
import json
import os
from datetime import datetime
from pathlib import Path

class ExperimentTracker:
    """轻量级实验追踪器（无需额外依赖）"""

    def __init__(self, experiment_dir="experiments"):
        self.experiment_dir = Path(experiment_dir)
        self.experiment_dir.mkdir(parents=True, exist_ok=True)

        timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
        self.run_dir = self.experiment_dir / f"run_{timestamp}"
        self.run_dir.mkdir()

        self.log_file = self.run_dir / "log.jsonl"
        self.config_file = self.run_dir / "config.json"
        self.metrics = []

    def log_config(self, config):
        """保存实验配置"""
        config["timestamp"] = datetime.now().isoformat()
        with open(self.config_file, 'w') as f:
            json.dump(config, f, indent=2)

    def log_metrics(self, step, metrics):
        """记录指标"""
        entry = {"step": step, **metrics}
        self.metrics.append(entry)
        with open(self.log_file, 'a') as f:
            f.write(json.dumps(entry) + '\n')

    def log_artifact(self, file_path, artifact_name=None):
        """保存文件产物"""
        import shutil
        name = artifact_name or Path(file_path).name
        dest = self.run_dir / "artifacts" / name
        dest.parent.mkdir(exist_ok=True)
        shutil.copy2(file_path, dest)

    def get_summary(self):
        """获取实验摘要"""
        return {
            "config": json.load(open(self.config_file)),
            "metrics_file": str(self.log_file),
            "total_steps": len(self.metrics),
        }
```

### 超参数调优策略

#### Optuna 调优

```python
import optuna

def objective(trial):
    """Optuna 优化目标函数"""
    # 定义搜索空间
    lr = trial.suggest_float("learning_rate", 1e-5, 1e-2, log=True)
    batch_size = trial.suggest_categorical("batch_size", [16, 32, 64, 128])
    n_layers = trial.suggest_int("n_layers", 1, 5)
    dropout = trial.suggest_float("dropout", 0.0, 0.5)
    optimizer_name = trial.suggest_categorical("optimizer", ["Adam", "SGD", "AdamW"])
    weight_decay = trial.suggest_float("weight_decay", 1e-6, 1e-3, log=True)

    # 构建模型
    model = build_model(n_layers=n_layers, dropout=dropout)
    optimizer = getattr(torch.optim, optimizer_name)(
        model.parameters(), lr=lr, weight_decay=weight_decay
    )

    # 训练和评估
    for epoch in range(50):
        train_loss = train_one_epoch(model, train_loader, optimizer)
        val_loss, val_acc = evaluate(model, val_loader)

        # 报告中间结果（用于剪枝）
        trial.report(val_acc, epoch)
        if trial.should_prune():
            raise optuna.TrialPruned()

    return val_acc

# 运行优化
study = optuna.create_study(
    direction="maximize",
    sampler=optuna.samplers.TPESampler(seed=42),
    pruner=optuna.pruners.MedianPruner(n_startup_trials=5),
)

study.optimize(objective, n_trials=100, timeout=3600*6)

# 分析结果
print(f"Best trial: {study.best_trial.number}")
print(f"Best value: {study.best_trial.value}")
print(f"Best params: {study.best_trial.params}")

# 可视化
optuna.visualization.plot_optimization_history(study)
optuna.visualization.plot_param_importances(study)
optuna.visualization.plot_parallel_coordinate(study)
```

#### 搜索空间设计指南

```markdown
## 超参数搜索空间建议

### 学习率 (Learning Rate)
- 范围: [1e-5, 1e-1]
- 采样: log-uniform (对数均匀)
- 典型值: 1e-3 (Adam), 0.1 (SGD with momentum)

### 批大小 (Batch Size)
- 选择: [16, 32, 64, 128, 256]
- 注意: 更大的 batch 需要更大的 learning rate

### 优化器 (Optimizer)
- 选择: [Adam, AdamW, SGD+Momentum, RAdam, LAMB]
- 注意: AdamW + cosine schedule 通常是好的默认选择

### 权重衰减 (Weight Decay)
- 范围: [1e-6, 1e-2]
- 采样: log-uniform
- 典型值: 1e-4 ~ 1e-3

### Dropout
- 范围: [0.0, 0.5]
- 采样: uniform
- 典型值: 0.1 ~ 0.3

### 网络深度/宽度
- 范围: 根据任务，通常 2-10 层
- 注意: 先小模型验证 pipeline，再增大
```

### 交叉验证模式

```python
import numpy as np
from sklearn.model_selection import (
    KFold, StratifiedKFold, GroupKFold,
    RepeatedStratifiedKFold, cross_validate
)

def cross_validation_report(X, y, model, cv_strategy='stratified_kfold',
                            n_splits=5, n_repeats=1, groups=None):
    """标准化的交叉验证报告"""
    from sklearn.metrics import make_scorer, accuracy_score, f1_score

    # 选择 CV 策略
    if cv_strategy == 'kfold':
        cv = KFold(n_splits=n_splits, shuffle=True, random_state=42)
    elif cv_strategy == 'stratified_kfold':
        cv = StratifiedKFold(n_splits=n_splits, shuffle=True, random_state=42)
    elif cv_strategy == 'group_kfold':
        cv = GroupKFold(n_splits=n_splits)
    elif cv_strategy == 'repeated_stratified':
        cv = RepeatedStratifiedKFold(n_splits=n_splits, n_repeats=n_repeats,
                                      random_state=42)

    # 评分指标
    scoring = {
        'accuracy': 'accuracy',
        'f1_macro': 'f1_macro',
        'f1_weighted': 'f1_weighted',
    }

    # 执行交叉验证
    results = cross_validate(
        model, X, y, cv=cv, scoring=scoring,
        return_train_score=True, return_estimator=True,
        groups=groups
    )

    # 输出报告
    print(f"\n{'='*60}")
    print(f"Cross-Validation Report ({cv_strategy}, {n_splits} folds)")
    print(f"{'='*60}")

    for metric in scoring:
        test_scores = results[f'test_{metric}']
        train_scores = results[f'train_{metric}']
        print(f"\n{metric}:")
        print(f"  Train: {train_scores.mean():.4f} ± {train_scores.std():.4f}")
        print(f"  Test:  {test_scores.mean():.4f} ± {test_scores.std():.4f}")
        print(f"  95% CI: [{test_scores.mean() - 1.96*test_scores.std():.4f}, "
              f"{test_scores.mean() + 1.96*test_scores.std():.4f}]")
        print(f"  Per-fold: {', '.join(f'{s:.4f}' for s in test_scores)}")

    return results

# CV 策略选择指南
"""
数据类型               推荐 CV 策略
──────────────────────────────────────────
平衡分类数据           StratifiedKFold
不平衡分类数据         RepeatedStratifiedKFold
分组数据(如多患者)     GroupKFold
时间序列数据           TimeSeriesSplit
小数据集(<100样本)     LeaveOneOut
标准回归任务           KFold
"""
```

### 结果报告标准

#### 实验结果表格模板

```markdown
## 主实验结果表 (Main Results Table)

| Method | Dataset 1 | Dataset 2 | Dataset 3 | Avg. | Params (M) | FLOPs (G) |
|--------|-----------|-----------|-----------|------|------------|-----------|
| Baseline A | 85.2±0.3 | 78.4±0.5 | 91.1±0.2 | 84.9 | 12.3 | 2.4 |
| Baseline B | 87.1±0.2 | 80.3±0.4 | 92.5±0.3 | 86.6 | 24.1 | 4.8 |
| Baseline C | 88.4±0.4 | 81.2±0.3 | 93.0±0.2 | 87.5 | 18.7 | 3.6 |
| **Ours**   | **91.3±0.2** | **84.5±0.3** | **95.2±0.1** | **90.3** | 15.6 | 3.1 |

报告格式：
- 准确率/精度: mean ± std (多次运行)
- 参数量: M (百万)
- FLOPs: G (十亿)
- 加粗最佳结果
- 可选: 下划线次佳结果

## 消融实验表 (Ablation Study)

| Variant | Acc. | Δ from Full |
|---------|------|-------------|
| Full model | 91.3 | — |
| w/o Module A | 89.1 | -2.2 |
| w/o Module B | 90.0 | -1.3 |
| w/o Module C | 90.5 | -0.8 |
| w/o A & B | 87.4 | -3.9 |
```

#### 统计显著性检验

```python
def compare_models(results_a, results_b, alpha=0.05):
    """比较两个模型的性能差异是否显著"""
    from scipy import stats

    # 配对 t-test（推荐用于 k-fold CV 结果比较）
    t_stat, p_value = stats.ttest_rel(results_a, results_b)

    print(f"Model A: {np.mean(results_a):.4f} ± {np.std(results_a):.4f}")
    print(f"Model B: {np.mean(results_b):.4f} ± {np.std(results_b):.4f}")
    print(f"t-statistic: {t_stat:.4f}")
    print(f"p-value: {p_value:.6f}")
    print(f"Significant: {'Yes' if p_value < alpha else 'No'}")

    # 效应量
    diff = np.array(results_a) - np.array(results_b)
    cohens_d = np.mean(diff) / np.std(diff, ddof=1)
    print(f"Cohen's d: {cohens_d:.3f}")

    return p_value < alpha
```

### 可复现性检查清单

```markdown
## Reproducibility Checklist

### 代码与环境
- [ ] 固定所有随机种子（Python, NumPy, PyTorch/TF, CUDA）
- [ ] 记录完整的依赖版本（requirements.txt / environment.yml）
- [ ] 记录硬件环境（GPU型号、CPU、内存）
- [ ] 记录软件版本（OS、CUDA、cuDNN、编译器）
- [ ] 代码公开或附带完整运行说明

### 数据
- [ ] 记录数据来源和版本
- [ ] 记录数据预处理步骤（含代码）
- [ ] 记录训练/验证/测试集划分方式
- [ ] 记录数据增强策略
- [ ] 如使用随机划分，固定随机种子

### 模型与训练
- [ ] 记录完整模型架构
- [ ] 记录所有超参数及其搜索空间
- [ ] 记录训练过程（损失曲线、最佳 checkpoint）
- [ ] 记录训练时间和计算资源消耗
- [ ] 记录模型参数量和 FLOPs

### 评估
- [ ] 使用标准评估指标和数据集
- [ ] 多次运行取均值和标准差（建议 ≥ 3 次，最佳 5 次）
- [ ] 进行统计显著性检验
- [ ] 报告置信区间
- [ ] 与公平的基线对比
```

#### 随机种子设置

```python
import random
import numpy as np
import torch

def set_seed(seed=42):
    """设置所有随机种子以确保可复现性"""
    random.seed(seed)
    np.random.seed(seed)
    torch.manual_seed(seed)
    torch.cuda.manual_seed_all(seed)
    torch.backends.cudnn.deterministic = True
    torch.backends.cudnn.benchmark = False
    # 环境变量
    import os
    os.environ['PYTHONHASHSEED'] = str(seed)
    os.environ['CUBLAS_WORKSPACE_CONFIG'] = ':4096:8'

def seed_worker(worker_id):
    """DataLoader worker 的种子设置"""
    worker_seed = torch.initial_seed() % 2**32
    np.random.seed(worker_seed)
    random.seed(worker_seed)

# DataLoader 使用
g = torch.Generator()
g.manual_seed(42)
loader = DataLoader(dataset, batch_size=32, num_workers=4,
                    worker_init_fn=seed_worker, generator=g)
```

### 实验目录结构

```
project/
├── configs/                    # 实验配置
│   ├── baseline.yaml
│   ├── exp001_lr_sweep.yaml
│   └── exp002_architecture.yaml
├── src/                        # 源代码
│   ├── models/
│   ├── data/
│   ├── trainers/
│   └── utils/
├── scripts/                    # 运行脚本
│   ├── train.py
│   ├── evaluate.py
│   └── sweep.py
├── experiments/                # 实验结果
│   ├── exp001_baseline/
│   │   ├── config.yaml         # 复制的配置
│   │   ├── train.log           # 训练日志
│   │   ├── metrics.json        # 指标记录
│   │   ├── checkpoints/        # 模型权重
│   │   └── figures/            # 可视化
│   ├── exp002_modified/
│   └── results_summary.csv     # 汇总表
├── data/                       # 数据
├── requirements.txt
└── README.md
```

### 论文实验章节模板

```markdown
## 4. Experiments

### 4.1 Datasets
We evaluate our method on three widely-used benchmarks:
- **Dataset A** (Smith et al., 2020): [描述，样本量，任务类型]
- **Dataset B** (Jones et al., 2021): [描述]
- **Dataset C** (Johnson et al., 2022): [描述]

We follow the standard train/val/test splits provided by each dataset.

### 4.2 Implementation Details
Our model is implemented in PyTorch 2.1 and trained on NVIDIA A100 GPUs.
We use AdamW optimizer with learning rate 3×10⁻⁴, weight decay 0.01,
and cosine learning rate schedule. The batch size is set to 32, and
models are trained for 100 epochs with early stopping (patience=10).
All experiments are repeated 5 times with different random seeds, and
we report mean ± standard deviation.

### 4.3 Baselines
We compare against the following methods:
- **Method A** (Author, 2023): [简述]
- **Method B** (Author, 2024): [简述]

### 4.4 Main Results
Table 1 shows the comparison results. Our method achieves the best
performance across all three datasets, with an average improvement of
X.X% over the strongest baseline. Specifically, on Dataset A, we
achieve XX.X% accuracy, outperforming Method B by X.X%.

### 4.5 Ablation Study
To validate the contribution of each component, we conduct ablation
experiments (Table 2). Removing Module A causes the largest performance
drop (-X.X%), confirming its importance. Module B and C contribute
X.X% and X.X% improvements, respectively.

### 4.6 Efficiency Analysis
Table 3 compares computational costs. Our method achieves a good
trade-off between accuracy and efficiency, requiring only XX% of the
parameters of Method B while achieving X.X% higher accuracy.

### 4.7 Visualization
Figure 3 visualizes the learned representations. Our method produces
more distinct cluster boundaries compared to baselines, indicating
better feature discrimination ability.
```

## Templates

### 实验配置 YAML 模板

```yaml
# configs/experiment.yaml
experiment:
  name: "exp001_baseline"
  seed: 42
  description: "Baseline with default hyperparameters"

model:
  architecture: "resnet50"
  pretrained: true
  num_classes: 10

training:
  optimizer: "AdamW"
  learning_rate: 3e-4
  weight_decay: 0.01
  batch_size: 32
  epochs: 100
  scheduler: "cosine"
  early_stopping_patience: 10
```

### 消融实验表模板

```markdown
| Variant | Acc. (%) | F1 | Params (M) | Δ from Full |
|---------|----------|-----|------------|-------------|
| Full model | 91.3 | 0.908 | 15.6 | — |
| w/o Module A | 89.1 | 0.883 | 12.1 | -2.2 |
| w/o Module B | 90.0 | 0.895 | 14.2 | -1.3 |
| w/o A & B | 87.4 | 0.862 | 10.7 | -3.9 |
```

### 实验结果提交模板

```python
def report_results(experiment_name, metrics, config):
    """标准化实验结果报告"""
    import json
    from datetime import datetime
    report = {
        "experiment": experiment_name,
        "timestamp": datetime.now().isoformat(),
        "config": config,
        "metrics": metrics,
        "environment": {"python": __import__('sys').version}
    }
    with open(f"results/{experiment_name}.json", 'w') as f:
        json.dump(report, f, indent=2)
```

## Common Patterns

### 实验管理流程

```
1. 假设形成 → 明确要验证什么
2. 实验设计 → 确定变量、指标、基线
3. 环境配置 → 记录所有依赖
4. 基线运行 → 确认 pipeline 正确
5. 新方法实现 → 模块化开发
6. 超参数调优 → 使用 Optuna/W&B
7. 结果分析 → 统计检验 + 可视化
8. 论文撰写 → 按报告标准
```

### 实验命名规范

```
格式: exp{编号}_{简要描述}
示例:
  exp001_baseline
  exp002_lr_sweep
  exp003_add_attention
  exp004_ablation_wo_dropout
  exp005_final_model
```

## Pitfalls to Avoid

1. **数据泄露**：测试集信息不能出现在训练/调优过程中
2. **过拟合验证集**：超参数调优过多轮次后可能过拟合验证集
3. **不公平对比**：对比方法应使用相同的数据划分和评估协议
4. **只报告最佳结果**：应报告多次运行的均值和标准差
5. **忽略训练时间**：应报告训练时间和推理速度
6. **超参数泄露**：在测试集上调优超参数等于数据泄露
7. **随机种子 cherry-picking**：不应选择"好看"的种子
8. **缺少消融实验**：应验证每个组件的贡献

## Resources

- [Weights & Biases Documentation](https://docs.wandb.ai/)
- [MLflow Documentation](https://mlflow.org/docs/latest/index.html)
- [Optuna Documentation](https://optuna.org/)
- [Sacred - Experiment Management](https://sacred.readthedocs.io/)
- [DVC - Data Version Control](https://dvc.org/)
- [ML Experiment Management Tools Comparison](https://neptune.ai/blog/best-ml-experiment-tracking-tools)
- [Papers With Code - SOTA Results](https://paperswithcode.com/sota)
