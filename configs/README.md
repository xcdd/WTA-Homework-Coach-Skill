# configs 目录说明（复用必读）

本目录是 `homework-coach` 的配置层，所有项目耦合信息必须在这里维护。

## 核心原则

1. `stages/*.md` 与 `SKILL.md` 不写绝对路径。
2. 路径、课次映射、项目别名均通过 `configs/*.md` 提供。
3. 迁移到新项目时，只改本目录，不改流程文件。

## 文件职责

- `project-homework.md`：Homework 根路径与 `HW/IN/STYLE/OUT` 别名定义（核心必需，缺则从 blank 复制）
- `lesson-map.md`：课次到必读素材的映射（核心必需，缺则从 blank 复制）
- `project-*.md`：按需项目配置，由 `lesson-map.md` 中出现的别名决定需要哪些
- `project-homework.blank.md`：Homework 配置空白模板，**首次复用时复制为 `project-homework.md` 并填写**
- `lesson-map.blank.md`：课次映射空白模板，**首次复用时复制为 `lesson-map.md` 并填写**
- `project-template.example.md`：任意项目的配置模板，**新增项目别名时复制为 `project-<别名>.md`**

## 复用步骤（迁移新项目）

1. 将 `configs/project-homework.blank.md` 复制为 `configs/project-homework.md`，填写根路径与 `HW/IN/STYLE/OUT`。
2. 将 `configs/lesson-map.blank.md` 复制为 `configs/lesson-map.md`，填写课次与必读素材。
3. `lesson-map.md` 中出现的每个项目别名，在 configs 下补齐对应 `project-<别名小写>.md`（可从 `project-template.example.md` 复制）。
4. 启动 Skill，阶段 00 会做配置完整性自检；缺文件时会提示复制上述模板。
