# APIMart API 配置说明

> 用于阶段 04 批量出图。配置文件为本 skill 根目录下的 `scripts/apimart.env`。

---

## 配置字段

```
API_URL: https://api.apimart.ai/v1/images/generations
MODEL: gemini-3-pro-image-preview
TOKEN: <你的 APIMart API Key>
# 兼容写法（可二选一）：
# SK: <你的 APIMart API Key>
# API_KEY: <你的 APIMart API Key>
RESOLUTION: 2K
SIZE: 16:9
N: 1
PAD_URL:
```

| 字段 | 说明 | 默认值 |
| --- | --- | --- |
| `API_URL` | APIMart 图片生成接口地址 | `https://api.apimart.ai/v1/images/generations` |
| `MODEL` | 使用的模型 | `gemini-3-pro-image-preview` |
| `TOKEN` | API 密钥主字段（**不要提交到版本控制**） | 无，必填其一 |
| `SK` / `API_KEY` | API 密钥兼容字段（与 `TOKEN` 等价） | 无，必填其一 |
| `RESOLUTION` | 图片分辨率 | `2K` |
| `SIZE` | 画幅比例 | `16:9` |
| `N` | 每个 prompt 生成几张图 | `1` |
| `PAD_URL` | 垫图 URL（可选） | 空 |

---

## 安全提醒

- 密钥（`TOKEN`/`SK`/`API_KEY`）是敏感信息，只放在 `scripts/apimart.env` 本地文件中
- 已在 `.gitignore` 中排除 `*.env` 文件
- 不要在聊天记录、文档或代码注释中暴露 TOKEN

---

## JSONL 请求格式

每行一张图，字段说明：

```jsonl
{"id":"01","prompt":"完整提示词内容","size":"16:9","n":1,"resolution":"2K","model":"gemini-3-pro-image-preview","pad_url":""}
```

| 字段 | 必填 | 说明 |
| --- | --- | --- |
| `id` | 否 | 图片编号，用于文件命名（不填则自动编号） |
| `prompt` | **是** | 完整的图片提示词 |
| `size` | 否 | 覆盖默认画幅 |
| `n` | 否 | 覆盖默认生成数量 |
| `resolution` | 否 | 覆盖默认分辨率 |
| `model` | 否 | 覆盖默认模型 |
| `pad_url` | 否 | 垫图 URL |
