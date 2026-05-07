---
name: character-image-prompt
description: Use when the user wants to analyze reference images for character image generation, create structured character prompts, build reusable character/outfit/scene/style/negative setting cards, or keep the same character, scene, outfit, or style consistent across a visual series. Trigger for requests involving 人物提示词, 参考图分析, 角色设定卡, 场景设定卡, 造型变体, 风格设定卡, 系列图一致性, or natural-language image prompt generation.
---

# Character Image Prompt

Use this skill to help the user turn reference images and natural-language intent into structured character image prompts, reusable setting cards, and consistent series prompts.

For the full rulebook, read `references/rulebook.md` when the task needs detailed behavior, templates, or edge-case rules.

## Core Workflow

1. If the user provides one or two reference images, analyze the image(s) first. Do not generate the final prompt yet.
2. Output a layered reference analysis: quick summary, detailed breakdown, extractable consistency anchors, adjustable elements, and confirmation question.
3. Wait for the user to confirm, modify, or add requirements.
4. Convert the user's natural-language intent into professional visual language: character, outfit, pose, camera, lighting, scene, color, texture, style keywords, and negative constraints.
5. Generate the final prompt using Chinese module descriptions plus English keyword reinforcement.
6. If the user likes a result or asks to reuse it, offer setting cards and generate drafts for confirmation before treating them as locked.

## Setting Card System

Use five card types:

- Core character setting card: who the character is.
- Outfit variant setting card: what the character wears in a specific theme or scene.
- Scene setting card: where the image takes place.
- Style setting card: how the image is visually rendered.
- Negative constraint card: what the image must avoid.

Setting cards are defaults, not cages. The user's current explicit request can temporarily override card content. Do not edit or replace an existing card unless the user explicitly asks to update it.

## Consistency Rules

When the user asks for the same character, same scene, same outfit, same style, series images, or only a changed action:

- State which cards or anchors are being reused.
- State what will change.
- Keep stable the requested identity, outfit, scene, and style anchors.
- Change only the requested variable, such as action, expression, gaze, pose, prop interaction, camera distance, or narrative moment.

For high consistency, suggest using the same reference image, locked setting cards, fixed seed, and platform-specific character/style reference features when available.

## Natural Language Calling

The user does not need to remember full card details. Match cards from names, aliases, colors, outfit clues, scene names, style tags, props, recent context, and keyword anchors.

Examples:

- "沈璃，白色那套，雪夜宫殿，回头看镜头。"
- "沿用这个角色和场景，只改变动作。"
- "保持角色不变，换成白色祭司造型。"

If one high-confidence match exists, call it and briefly explain. If multiple candidates exist, ask a short clarification. If no match exists, say so and offer to create a new card or use a temporary description.

## Final Prompt Structure

Use this default output structure:

```md
## 基础画面设定
## 核心角色一致性
## 当前造型设定
## 主体关系与画面中心
## 姿态、动作与叙事
## 摄影构图与镜头
## 灯光系统
## 场景与空间系统
## 色彩与视觉焦点
## 画面质感与英文关键词
## 负面约束
```

If no locked core character card is involved, `核心角色一致性` may become `人物外观系统`.

## Output Rules

- Use Chinese for structure, intent, and visual logic.
- Use English keywords only as precise reinforcement for style, camera, lighting, material, texture, and quality.
- Do not over-stack generic quality words.
- Keep negative constraints relevant to the task.
- If the user specifies a target platform, adapt the final format while preserving the core visual logic.

## Safety And Copyright

When analyzing reference images, extract transferable visual rules instead of copying unique protected character designs, trademarks, logos, or identifiable people. Note uncertainty when visual details are ambiguous.
