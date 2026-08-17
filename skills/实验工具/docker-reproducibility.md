# Docker 可复现性

> Category: 实验工具 | Difficulty: intermediate | Last updated: 2026

## When to Use

当用户需要使用 Docker 容器化机器学习实验、创建可复现的研究环境或多服务部署时使用此技能。适用于实验环境复现、论文代码封装、GPU 实验容器化、多服务协作等场景。当用户提及 Docker、容器化、可复现环境、reproducibility、Dockerfile、docker-compose、GPU 支持 或 environment isolation 时触发。

## Instructions for AI Assistant

### 基本原则

1. **最小镜像**：选择合适的基础镜像，减小体积
2. **分层构建**：善用 Docker cache，优化构建速度
3. **安全性**：不使用 root 用户，不暴露敏感信息
4. **可复现性**：固定所有依赖版本
5. **GPU 支持**：正确配置 NVIDIA Container Toolkit

### Dockerfile 模板

#### Python 机器学习项目（通用）

```dockerfile
# ============================================
# Python ML Project Dockerfile
# ============================================

# --- Stage 1: Builder ---
FROM python:3.11-slim AS builder

WORKDIR /build

# 安装系统依赖
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# 先复制依赖文件（利用 Docker cache）
COPY requirements.txt .
RUN pip install --no-cache-dir --prefix=/install -r requirements.txt

# --- Stage 2: Runtime ---
FROM python:3.11-slim

# 设置环境变量
ENV PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    PIP_NO_CACHE_DIR=1

# 安装运行时系统依赖
RUN apt-get update && apt-get install -y --no-install-recommends \
    libgomp1 \
    libgl1-mesa-glx \
    libglib2.0-0 \
    && rm -rf /var/lib/apt/lists/*

# 从 builder 复制 Python 包
COPY --from=builder /install /usr/local

# 创建非 root 用户
RUN groupadd -r mluser && useradd -r -g mluser -d /home/mluser mluser
RUN mkdir -p /home/mluser/app && chown -R mluser:mluser /home/mluser

WORKDIR /home/mluser/app

# 复制项目文件
COPY --chown=mluser:mluser . .

# 切换到非 root 用户
USER mluser

# 默认命令
CMD ["python", "train.py"]
```

#### PyTorch + CUDA GPU 项目

```dockerfile
# ============================================
# PyTorch GPU Project Dockerfile
# ============================================
FROM nvidia/cuda:12.2.0-cudnn8-runtime-ubuntu22.04

# 避免交互式安装
ENV DEBIAN_FRONTEND=noninteractive

# 系统依赖
RUN apt-get update && apt-get install -y --no-install-recommends \
    python3.11 \
    python3.11-venv \
    python3-pip \
    git \
    wget \
    libglib2.0-0 \
    libsm6 \
    libxext6 \
    libxrender1 \
    && rm -rf /var/lib/apt/lists/* \
    && ln -sf /usr/bin/python3.11 /usr/bin/python

# 升级 pip
RUN python -m pip install --upgrade pip

WORKDIR /app

# 安装 PyTorch（匹配 CUDA 版本）
COPY requirements.txt .
RUN pip install --no-cache-dir \
    torch==2.1.0+cu121 \
    torchvision==0.16.0+cu121 \
    --index-url https://download.pytorch.org/whl/cu121 \
    && pip install --no-cache-dir -r requirements.txt

# 复制代码
COPY . .

# 配置
ENV NVIDIA_VISIBLE_DEVICES=all \
    NVIDIA_DRIVER_CAPABILITIES=compute,utility \
    CUDA_VISIBLE_DEVICES=0

# 默认命令
CMD ["python", "train.py", "--config", "configs/default.yaml"]
```

#### TensorFlow + GPU

```dockerfile
# ============================================
# TensorFlow GPU Dockerfile
# ============================================
FROM tensorflow/tensorflow:2.15.0-gpu

# 系统依赖
RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    wget \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

# 安装 Python 依赖
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# 复制代码
COPY . .

CMD ["python", "train.py"]
```

#### R 统计分析项目

```dockerfile
# ============================================
# R Statistical Analysis Dockerfile
# ============================================
FROM rocker/r-ver:4.3.2

# 系统依赖
RUN apt-get update && apt-get install -y --no-install-recommends \
    libcurl4-openssl-dev \
    libssl-dev \
    libxml2-dev \
    libfontconfig1-dev \
    libharfbuzz-dev \
    libfribidi-dev \
    libfreetype6-dev \
    libpng-dev \
    libtiff5-dev \
    libjpeg-dev \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

# 安装 R 包
COPY renv.lock .
RUN Rscript -e "install.packages('renv')" \
    && Rscript -e "renv::restore(lockfile='renv.lock')"

# 复制代码
COPY . .

CMD ["Rscript", "analysis.R"]
```

### docker-compose 多服务模板

#### ML 实验 + 监控 + 可视化

```yaml
# docker-compose.yml
version: '3.8'

services:
  # === 训练服务 ===
  trainer:
    build:
      context: .
      dockerfile: Dockerfile
    container_name: ml-trainer
    volumes:
      - ./data:/app/data:ro           # 只读数据
      - ./output:/app/output           # 输出目录
      - ./configs:/app/configs:ro      # 配置文件
      - ./logs:/app/logs               # 日志目录
    environment:
      - WANDB_API_KEY=${WANDB_API_KEY}
      - CUDA_VISIBLE_DEVICES=0
      - PYTHONPATH=/app
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: 1
              capabilities: [gpu]
        limits:
          memory: 16G
    command: python train.py --config configs/default.yaml
    networks:
      - ml-net

  # === Jupyter 开发环境 ===
  jupyter:
    build:
      context: .
      dockerfile: Dockerfile
    container_name: ml-jupyter
    ports:
      - "8888:8888"
    volumes:
      - .:/app
    environment:
      - JUPYTER_TOKEN=${JUPYTER_TOKEN:-research}
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: 1
              capabilities: [gpu]
    command: >
      jupyter lab --ip=0.0.0.0 --port=8888
      --no-browser --allow-root
      --NotebookApp.token=${JUPYTER_TOKEN:-research}
    networks:
      - ml-net

  # === TensorBoard ===
  tensorboard:
    image: tensorflow/tensorflow:2.15.0
    container_name: ml-tensorboard
    ports:
      - "6006:6006"
    volumes:
      - ./logs:/logs
    command: tensorboard --logdir=/logs --host=0.0.0.0 --port=6006
    networks:
      - ml-net

  # === MLflow 追踪服务器 ===
  mlflow:
    image: ghcr.io/mlflow/mlflow:v2.9.2
    container_name: ml-mlflow
    ports:
      - "5000:5000"
    volumes:
      - ./mlruns:/mlflow/mlruns
    command: mlflow server --host 0.0.0.0 --port 5000
    networks:
      - ml-net

networks:
  ml-net:
    driver: bridge
```

#### 数据处理 Pipeline

```yaml
# docker-compose.pipeline.yml
version: '3.8'

services:
  # 数据库
  postgres:
    image: postgres:16-alpine
    container_name: ml-postgres
    environment:
      POSTGRES_DB: ml_experiment
      POSTGRES_USER: mluser
      POSTGRES_PASSWORD: ${DB_PASSWORD}
    volumes:
      - postgres_data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U mluser"]
      interval: 5s
      timeout: 5s
      retries: 5

  # Redis 缓存
  redis:
    image: redis:7-alpine
    container_name: ml-redis
    ports:
      - "6379:6379"

  # MinIO 对象存储（S3 兼容）
  minio:
    image: minio/minio:latest
    container_name: ml-minio
    ports:
      - "9000:9000"
      - "9001:9001"
    environment:
      MINIO_ROOT_USER: minioadmin
      MINIO_ROOT_PASSWORD: ${MINIO_PASSWORD}
    volumes:
      - minio_data:/data
    command: server /data --console-address ":9001"

volumes:
  postgres_data:
  minio_data:
```

### 环境变量管理

```markdown
## 环境变量配置

### .env 文件（不要提交到 git）
```env
# API Keys
WANDB_API_KEY=wand_xxxxxxxxxxxxx
HF_TOKEN=hf_xxxxxxxxxxxxx

# Database
DB_PASSWORD=secure_password_here
MINIO_PASSWORD=minio_secure_password

# Compute
CUDA_VISIBLE_DEVICES=0
NVIDIA_VISIBLE_DEVICES=all

# Paths
DATA_DIR=/data/datasets
OUTPUT_DIR=/output
```

### .env.example（提交到 git 的模板）
```env
# API Keys (get from respective services)
WANDB_API_KEY=your_wandb_key_here
HF_TOKEN=your_huggingface_token_here

# Database
DB_PASSWORD=change_me
MINIO_PASSWORD=change_me

# Compute
CUDA_VISIBLE_DEVICES=0

# Paths
DATA_DIR=./data
OUTPUT_DIR=./output
```

### 使用方法
```bash
# docker-compose 自动读取 .env
docker compose up

# 或手动指定
docker compose --env-file .env.production up
```
```

### Volume 挂载策略

```markdown
## Volume 挂载最佳实践

### 数据卷（只读）
```yaml
volumes:
  - ./data:/app/data:ro           # 训练数据（只读）
  - ./pretrained:/app/pretrained:ro  # 预训练模型（只读）
```

### 输出卷（读写）
```yaml
volumes:
  - ./output:/app/output           # 模型输出
  - ./logs:/app/logs               # 训练日志
  - ./checkpoints:/app/checkpoints  # 模型权重
```

### 命名卷（持久化）
```yaml
volumes:
  - pip_cache:/root/.cache/pip     # pip 缓存
  - huggingface_cache:/root/.cache/huggingface  # HF 缓存

volumes:
  pip_cache:
  huggingface_cache:
```

### 性能优化
```yaml
# Linux 上使用 :cached 提升 macOS 性能
volumes:
  - ./data:/app/data:cached

# 使用 tmpfs 挂载临时文件
tmpfs:
  - /tmp:size=1G
```
```

### GPU 支持配置

```markdown
## GPU 支持设置

### 前置条件
1. 安装 NVIDIA 驱动
2. 安装 NVIDIA Container Toolkit:
```bash
# Ubuntu
distribution=$(. /etc/os-release; echo $ID$VERSION_ID)
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | \
    sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg
curl -s -L https://nvidia.github.io/libnvidia-container/$distribution/libnvidia-container.list | \
    sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' | \
    sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
sudo apt-get update
sudo apt-get install -y nvidia-container-toolkit
sudo systemctl restart docker
```

### docker-compose GPU 配置
```yaml
services:
  trainer:
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: all       # 或指定数量: 2
              capabilities: [gpu, compute, utility]
```

### 验证 GPU 可用
```bash
# 检查 NVIDIA 驱动
nvidia-smi

# 检查 Docker GPU 支持
docker run --rm --gpus all nvidia/cuda:12.2.0-base-ubuntu22.04 nvidia-smi

# PyTorch 检查
docker run --rm --gpus all your-image python -c \
    "import torch; print(f'CUDA: {torch.cuda.is_available()}, GPUs: {torch.cuda.device_count()}')"
```

### 多 GPU 训练
```yaml
# DataParallel
environment:
  - CUDA_VISIBLE_DEVICES=0,1,2,3

# DistributedDataParallel
command: torchrun --nproc_per_node=4 train.py --distributed
deploy:
  resources:
    reservations:
      devices:
        - driver: nvidia
          count: 4
          capabilities: [gpu]
```
```

### .dockerignore

```markdown
## .dockerignore 文件

```
# Git
.git
.gitignore

# Python
__pycache__
*.py[cod]
*.egg-info
dist/
build/
.eggs/
*.egg

# Virtual environments
.venv/
venv/
env/

# IDE
.idea/
.vscode/
*.swp
*.swo

# Jupyter
.ipynb_checkpoints/

# Data (构建时不需要大数据)
data/
datasets/
*.h5
*.hdf5
*.pkl
*.parquet

# Models (大型模型文件)
pretrained/
checkpoints/
*.pt
*.pth
*.bin
*.onnx

# Logs and output
logs/
output/
mlruns/
wandb/

# Docker
Dockerfile
docker-compose*.yml
.dockerignore

# Documentation
README.md
docs/
*.md
LICENSE
```
```

### 构建和运行命令

```bash
## 常用 Docker 命令

### 构建镜像
# 基本构建
docker build -t my-ml-project:latest .

# 指定 Dockerfile
docker build -f Dockerfile.gpu -t my-ml-project:gpu .

# 带构建参数
docker build --build-arg PYTHON_VERSION=3.11 -t my-ml-project .

# 不使用缓存（全新构建）
docker build --no-cache -t my-ml-project .

### 运行容器
# 基本运行
docker run --rm my-ml-project

# 带 GPU
docker run --rm --gpus all my-ml-project

# 交互模式（调试）
docker run --rm -it --gpus all my-ml-project /bin/bash

# 带挂载
docker run --rm --gpus all \
    -v $(pwd)/data:/app/data:ro \
    -v $(pwd)/output:/app/output \
    my-ml-project

# 后台运行
docker run -d --name trainer --gpus all \
    -v $(pwd)/data:/app/data:ro \
    -v $(pwd)/output:/app/output \
    my-ml-project

### docker-compose
# 启动所有服务
docker compose up -d

# 查看日志
docker compose logs -f trainer

# 停止
docker compose down

# 重建并启动
docker compose up -d --build

# 只启动特定服务
docker compose up -d jupyter tensorboard
```

### 镜像优化技巧

```markdown
## 镜像大小优化

### 多阶段构建
- Builder 阶段安装编译依赖
- Runtime 阶段只保留运行时依赖
- 可减少 50-70% 的镜像大小

### 选择正确的基础镜像
| 镜像 | 大小 | 场景 |
|------|------|------|
| python:3.11 | ~1GB | 通用开发 |
| python:3.11-slim | ~150MB | 生产环境 |
| python:3.11-alpine | ~50MB | 最小部署（注意兼容性）|

### 减少层数
```dockerfile
# ✓ 合并 RUN 指令
RUN apt-get update && apt-get install -y \
    package1 \
    package2 \
    && rm -rf /var/lib/apt/lists/*

# ✗ 分开写
RUN apt-get update
RUN apt-get install -y package1
RUN apt-get install -y package2
```

### 使用 .dockerignore
排除不必要的文件（数据、模型、日志等）
```

## Templates

### 最小可用 Dockerfile 模板

```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
CMD ["python", "train.py"]
```

### GPU 实验 docker-compose 快速模板

```yaml
version: '3.8'
services:
  trainer:
    build: .
    volumes:
      - ./data:/app/data:ro
      - ./output:/app/output
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: 1
              capabilities: [gpu]
    command: python train.py
```

### 一键构建并验证脚本模板

```bash
#!/bin/bash
IMAGE_NAME="ml-project:latest"
docker build -t $IMAGE_NAME . && \
docker run --rm --gpus all $IMAGE_NAME python -c \
  "import torch; print(f'CUDA: {torch.cuda.is_available()}')"
echo "Image $IMAGE_NAME built and verified."
```

## Common Patterns

### 可复现实验的标准流程

```
1. 编写 requirements.txt → 固定版本
2. 创建 Dockerfile → 多阶段构建
3. 编写 docker-compose.yml → 服务编排
4. 创建 .env.example → 环境变量模板
5. 编写 .dockerignore → 排除大文件
6. 构建并测试 → docker compose up
7. 记录构建信息 → 写入 README
```

### 实验代码的 Docker 化检查清单

```markdown
## Dockerization Checklist

- [ ] Dockerfile 存在且可构建
- [ ] requirements.txt 固定所有版本
- [ ] .dockerignore 排除不必要文件
- [ ] 数据通过 volume 挂载（不 COPY 到镜像）
- [ ] 输出通过 volume 持久化
- [ ] GPU 配置正确（如需要）
- [ ] 非 root 用户运行
- [ ] 环境变量模板 (.env.example) 存在
- [ ] README 包含 Docker 使用说明
- [ ] 构建和运行命令已测试
```

## Pitfalls to Avoid

1. **不固定版本**：使用 `pip install torch` 而非 `pip install torch==2.1.0` 导致不可复现
2. **大数据 COPY 到镜像**：应使用 volume 挂载，避免镜像过大
3. **root 用户运行**：生产环境应使用非 root 用户
4. **暴露敏感信息**：API key 不应写在 Dockerfile 中，使用环境变量
5. **忽略 .dockerignore**：导致不必要的文件进入构建上下文，拖慢构建
6. **单层构建**：不利用 Docker cache，每次修改都全量重建
7. **忽略 GPU 驱动版本**：CUDA 版本与驱动版本不匹配导致 GPU 不可用
8. **固定端口号**：应使用环境变量配置端口

## Resources

- [Docker 官方文档](https://docs.docker.com/)
- [Docker Compose 文档](https://docs.docker.com/compose/)
- [NVIDIA Container Toolkit](https://github.com/NVIDIA/nvidia-container-toolkit)
- [Docker Best Practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- [NVIDIA NGC Containers](https://catalog.ngc.nvidia.com/)
- [Reproducible Research with Docker - The Turing Way](https://the-turing-way.netlify.app/reproducible-research/renv/renv-docker.html)
