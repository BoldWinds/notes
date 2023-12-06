# conda常用命令

## 创建相关

创建一个conda环境：

```bash
conda create --name myenv python=3.11
```

导出conda环境：

```bash
conda env export > environment.yml
```

从yml创建环境：

```bash
conda env create -f environment.yml
```

