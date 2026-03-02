# 项目路径配置：Homework（运行配置）

> 这是发布包默认运行配置。请先把占位符替换为你自己的实际路径再启动 Skill。

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
