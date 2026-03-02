# 项目路径配置模板（可复用）

> 复制为 `project-<name>.md` 后填写。仅作为模板，不直接参与运行。

## 项目标识

- `project_id`: `<project-id>`
- `project_name`: `<project-name>`

## 根路径

- `root`: `<absolute-or-workspace-relative-path>`

## 别名定义

- `<ALIAS>/` -> `<root-or-subpath>`

## 可选：高频文档定位

- `<ALIAS>/README.md`
- `<ALIAS>/docs/`

## 使用规则

1. 流程文件只使用别名，不写绝对路径。
2. 项目迁移时仅修改本文件。
