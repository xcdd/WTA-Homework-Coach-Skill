# 项目路径配置：Homework（空白模板）

> 首次复用时：复制本文件为 `project-homework.md`，填写下方占位符。本文件不参与运行。

## 项目标识

- `project_id`: `homework`
- `project_name`: `<你的工作区名称，如 MyCourse-Homework>`

## 根路径

- `root`: `<Homework 目录的绝对路径，如 D:/MyProject/Homework>`

## 别名定义

- `HW/` -> `<同上 root>`
- `IN/` -> `<HW 下的输入目录，如 HW/ai-learn/OtherINPUT>`
- `STYLE/` -> `<HW 下的文风参考目录，如 HW/ai-learn/HistoricalArticles>`
- `OUT/` -> `<HW 下的输出目录，如 HW/ai-output>`

## 使用规则

1. 流程文件中只使用别名（`HW/IN/STYLE/OUT`），不要写绝对路径。
2. 若目录迁移，仅更新本文件，不改 `stages/*.md`。
3. 启动阶段必须先读取本文件再解析路径。
