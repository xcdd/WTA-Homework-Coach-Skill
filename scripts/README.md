# APIMart 批量出图脚本

用于 homework-coach Skill 阶段 04（配图生成）的批量图片生成。

## 前提

- Python 3.8+
- APIMart API Key（在 [APIMart](https://apimart.ai) 获取）

## 配置

1. 复制配置模板：

```bash
cp scripts/apimart.env.example scripts/apimart.env
```

PowerShell 可用：

```powershell
Copy-Item "scripts/apimart.env.example" "scripts/apimart.env"
```

2. 编辑 `scripts/apimart.env`，填入密钥（`TOKEN` 或 `SK` 或 `API_KEY`）

## 使用

### 正常出图

```bash
python scripts/apimart_batch_generate.py \
  --config scripts/apimart.env \
  --input "<requests.jsonl 的实际路径>" \
  --out "<图片输出目录的实际路径>"
```

### 预览模式（不调用 API，只生成 curl 命令）

```bash
python scripts/apimart_batch_generate.py \
  --config scripts/apimart.env \
  --input "<requests.jsonl 的实际路径>" \
  --dry-run
```

> 注意：`OUT/` 是 Skill 文档里的逻辑别名，不是终端可直接解析的路径。命令行里请填写真实文件路径。

## 输入格式（JSONL）

每行一张图：

```jsonl
{"id":"01","prompt":"...","size":"16:9","n":1,"resolution":"2K","model":"gemini-3-pro-image-preview"}
```

最少只需要 `prompt` 字段，其他字段不填则使用 `.env` 中的默认值。

## 输出

- 图片文件保存在 `--out` 指定的目录（默认 `outputs/`）
- `run.json` 记录所有请求和返回信息
