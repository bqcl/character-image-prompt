# Character Image Prompt Skill

一个用于人物图像提示词生成的 Codex skill。

它支持参考图分析、自然语言需求转译、结构化人物提示词生成、设定卡创建，以及同一角色/场景/风格在系列图中的一致性维护。

## 功能

- 分析 1-2 张参考图，并先等待用户确认
- 将自然语言审美描述转译为专业视觉语言
- 生成“中文模块说明 + 英文关键词补强”的人物图像提示词
- 创建可复用设定卡：
  - 核心角色设定卡
  - 造型变体设定卡
  - 场景设定卡
  - 风格设定卡
  - 负面约束卡
- 支持自然语言调用设定卡
- 支持同一角色、同一场景、不同动作的系列图提示词生成

## 目录结构

```text
character-image-prompt/
  SKILL.md
  references/
    rulebook.md
```

`SKILL.md` 是 skill 入口，包含触发描述和精简工作流。

`references/rulebook.md` 是完整规则说明书，包含参考图分析、设定卡体系、提示词输出结构、负面约束和质量检查规则。

## 安装

将整个 `character-image-prompt` 文件夹复制到 Codex skills 目录：

```text
~/.codex/skills/character-image-prompt/
```

Windows 示例：

```text
C:\Users\<YourName>\.codex\skills\character-image-prompt\
```

安装后目录应类似：

```text
.codex/
  skills/
    character-image-prompt/
      SKILL.md
      references/
        rulebook.md
```

## 使用示例

分析参考图：

```text
使用 character-image-prompt skill，帮我分析这张参考图。
先分析，不要直接生成最终提示词。
```

直接生成提示词：

```text
请根据 character-image-prompt skill 生成人物图像提示词。
需求：一个清冷、危险、有东方贵族感的女性角色，站在雪夜宫殿中，整体要电影感和高级时尚摄影质感。
```

建立设定卡：

```text
这张满意。请提取核心角色设定卡、造型变体设定卡、场景设定卡和风格设定卡草稿。
```

调用设定卡：

```text
沿用沈璃这个角色，使用白色祭司造型，场景是雪夜宫殿。
这次只改变动作：让她回头看向镜头。
```

## 设定卡原则

设定卡是默认锚点，不是不可修改的限制。

如果用户当前明确要求改变某项内容，当前要求优先。临时变化不会自动覆盖原设定卡，除非用户明确要求更新或保存为新设定卡。
