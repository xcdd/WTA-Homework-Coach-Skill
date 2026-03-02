# Export Manifest

本文件定义 WTA-Homework-Coach-Skill 发布包的边界，确保发布时不带入本地实例与敏感信息。

## 发布目录

- `publish/homework-coach-github/`（仓库根目录即 skill 根目录）

## 已包含（可直接发布）

- `SKILL.md`
- `docx-to-md.md`
- `stages/*.md`
- `templates/*.md`
- `scripts/apimart_batch_generate.py`
- `scripts/apimart.env.example`
- `scripts/README.md`
- `configs/README.md`
- `configs/project-homework.blank.md`
- `configs/lesson-map.blank.md`
- `configs/project-template.example.md`
- `configs/lesson-map.example.md`
- `configs/project-homework.md`（占位运行配置）
- `configs/lesson-map.md`（占位运行配置）
- `README.md`、`LICENSE`、`CONTRIBUTING.md`、`.gitignore`、`examples/`（本 skill 不提供 SECURITY.md）

## 默认排除（不得发布）

以下文件属于当前用户本地实例配置，不应进入公开仓库：

- 任何含本机绝对路径或私有项目结构的 `configs/project-*.md`
- 任何含私有项目资料路径的 `configs/lesson-map.md`
- `scripts/apimart.env`（真实密钥文件）
- 运行产物（如图片、`run.json`、临时请求文件）

## 发布前核查

1. 不含本机绝对路径（例如盘符开头路径）
2. 不含真实密钥（`TOKEN` 仅允许占位符）
3. 启动最小流程可跑通（至少到阶段 01）
