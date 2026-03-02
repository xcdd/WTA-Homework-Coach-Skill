# 图片提示词风格块

> 阶段 04 生成图片提示词时，每张图必须以本文件定义的风格作为**唯一允许的基础风格**。
> 不得让模型自行切换成其他风格。

---

## 默认风格基准

```
Style: Cream-colored paper texture background (visible paper grain).
Line art in colored pencil (visible pencil strokes), with soft watercolor fills (light washes, gentle blending).
Warm color palette. Light doodle decorations for warmth and personality.
Clean and approachable, NOT corporate or sterile.

Layout: 16:9 horizontal format.
Generous whitespace. Clear visual hierarchy.
Cards/sections aligned neatly. Arrows and connectors are bold and easy to follow.

Text: All Chinese text must be clearly legible, no garbled characters.
Large font size. Short phrases only. NO dense paragraphs or tiny annotations.
Only include the exact text specified — do NOT generate any additional text, labels, watermarks, or signatures.

Negative constraints:
- NO flat vector/poster style
- NO 3D rendering
- NO photorealistic style
- NO complex backgrounds or strong gradient lighting
- NO extra small text annotations, watermarks, or signatures
- NO English text or random characters
```

---

## 可选风格变体

如果用户要求不同风格，以下是允许的变体（替换默认风格块）：

### 极简线稿风

```
Style: Clean white background. Thin black ink line drawings, minimal color accents.
Modern, minimal, diagram-like. No texture, no watercolor.
```

### 科技蓝风

```
Style: Dark navy blue background. Neon-accent wireframe elements.
Futuristic, tech-oriented. Glowing edges on cards and connectors.
Still maintain legible Chinese text with high contrast.
```

---

## 风格锁定规则

1. 每张图的提示词中必须包含完整的风格块（不能省略）
2. 同一篇作业的所有配图使用**同一风格**，保持视觉一致性
3. 如果用户没指定风格，用默认风格基准
4. 明确写"This is the ONLY allowed style. Do NOT switch to flat vector, 3D, or photorealistic."

---

## 使用方式

在阶段 04 生成提示词时，将本文件的风格块粘贴到每张提示词的开头，然后追加具体内容描述、文字要求和排版约束。

示例组装：

```
[风格块（从本文件复制）]

Content: An overview diagram showing the 3-stage user onboarding flow.
Stage 1: "发现痛点" with a magnifying glass icon.
Stage 2: "制定计划" with a clipboard icon.
Stage 3: "开始行动" with a rocket icon.

Text on image (exact Chinese characters, mandatory):
- Title: "用户引导三步走"
- Stage labels: "发现痛点", "制定计划", "开始行动"
- No other text allowed.

Layout: 3 cards arranged horizontally, connected by arrows. Title centered at top.
```
