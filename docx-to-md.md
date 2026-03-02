# docx-to-md 转换协议

> 本文件是 homework-coach Skill 的子模块，按需调用。
> 当用户传入 `.docx` 文件时，主 Skill 应引用本文件执行转换。

## 触发条件

以下任一情况触发本协议：
- 用户将 `.docx` 文件放入 `IN/` 或 `STYLE/`
- Skill 启动时发现目录中有 `.docx` 文件但没有同名 `.md` 文件
- 用户明确要求转换

## 转换流程

### 1. 安装依赖（首次）

```bash
pip install python-docx
```

### 2. 执行转换脚本

在工作区根目录创建临时脚本 `_convert_docx.py` 并执行：

```python
# -*- coding: utf-8 -*-
import docx, os, glob, sys

target_dir = sys.argv[1] if len(sys.argv) > 1 else '.'
docx_files = glob.glob(os.path.join(target_dir, '*.docx'))

for src in docx_files:
    dst = src.replace('.docx', '.md')
    if os.path.exists(dst):
        print(f'SKIP: {os.path.basename(src)} (md already exists)')
        continue
    try:
        doc = docx.Document(src)
        lines = []
        for para in doc.paragraphs:
            text = para.text.strip()
            style = para.style.name if para.style else ''
            if 'Heading 1' in style:
                lines.append(f'# {text}')
            elif 'Heading 2' in style:
                lines.append(f'## {text}')
            elif 'Heading 3' in style:
                lines.append(f'### {text}')
            elif 'List' in style:
                lines.append(f'- {text}')
            else:
                lines.append(text)
        for table in doc.tables:
            lines.append('')
            for i, row in enumerate(table.rows):
                cells = [cell.text.strip().replace('\n', ' ') for cell in row.cells]
                lines.append('| ' + ' | '.join(cells) + ' |')
                if i == 0:
                    lines.append('| ' + ' | '.join(['---'] * len(cells)) + ' |')
            lines.append('')
        with open(dst, 'w', encoding='utf-8') as out:
            out.write('\n'.join(lines))
        print(f'OK: {os.path.basename(src)}')
    except Exception as e:
        print(f'FAIL: {os.path.basename(src)} -> {e}')
```

执行方式：
```bash
python _convert_docx.py "{IN_DIR}"
python _convert_docx.py "{STYLE_DIR}"
```

说明：
- `{IN_DIR}`、`{STYLE_DIR}` 来自 `configs/project-homework.md` 的别名解析结果
- 不要在转换命令中写死 `Homework/...` 目录

### 3. 转换后清理

- 删除临时脚本 `_convert_docx.py`
- 保留原始 `.docx` 文件（用户可能需要）

### 4. 邀请用户评估完整性

转换完成后，**必须**向用户展示以下信息并请求确认：

```
已完成 docx → md 转换：
- [文件名1].docx → [文件名1].md（XX行）
- [文件名2].docx → [文件名2].md（XX行）

请检查以下内容：
1. 打开生成的 .md 文件，确认文字内容是否完整
2. 原文中的表格是否正确转换（docx 中的复杂合并单元格可能丢失）
3. 原文中的图片无法转换，如有重要图片请手动补充说明
4. 如有内容缺失或格式错误，请告知我具体位置

确认完整后我再继续后续流程。
```

**用户确认完整性之前，不得使用转换后的 .md 文件作为写作素材。**

## 已知限制

- `.docx` 中的图片不会被提取（会显示为空）
- 复杂的合并单元格表格可能格式错乱
- 嵌入的 OLE 对象（如 Excel 图表）不会被转换
- 文件名含特殊标点时，路径解析可能失败（用 glob 模式匹配规避）
