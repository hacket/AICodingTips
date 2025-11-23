---
banner:
date_created: Thursday, October 23rd 2025, 11:41:56 pm
date_updated: Monday, November 17th 2025, 12:13:18 am
title: Claude Code Skills个人总结
author: hacket
categories:
  - AI
category: ClaudeCode
tags: [AI, ClaudeCode]
toc: true
description:
dg-publish: true
dg-enable-search: true
dg-show-local-graph: true
dg-show-toc: true
dg-show-file-tree: true
image-auto-upload: true
feed: show
format: list
aliases: [Claude Code Skills]
linter-yaml-title-alias: Claude Code Skills
---

# Claude Code Skills

## Skills 是什么？

progressive disclosure

两篇关于 Skill 的好文章:

- Skills explained: How Skills compares to prompts, Projects, MCP, and subagents <https://claude.com/blog/skills-explained>
- Claude Skills 不就是把提示词存个文件夹吗？ <https://mp.weixin.qq.com/s/UjZAqvkfk8AzpOoK1KV0yw?scene=0&subscene=90>

其他：

- [Claude Skills are awesome, maybe a bigger deal than MCP](https://simonwillison.net/2025/Oct/16/claude-skills/?s=09)

## Skills 用途

### 企业应用

- 品牌一致性
	- 自动套用公司的品牌颜色、字体、Logo 位置
	- 示例：「帮我做一份 Q3 报告的 PPT，用公司的品牌风格」
- 标准化文件
	- 自动生成符合公司格式的会议记录、状态报告
	- 示例：「写一份给客户的周报，用我们的标准格式」
- 工作流程自动化
	- 在项目管理工具（JIRA、Asana）中按照团队惯例创建任务
	- 执行公司特定的数据分析流程

### 创意设计

- 生成式艺术：使用 p5.js 创作艺术作品
- 设计规范：按照设计哲学创建视觉素材
- 动画制作：制作符合 Slack 尺寸限制的 GIF

### 技术开发

- 代码测试：使用 Playwright 测试网页应用
- 文件处理：创建和编辑 Excel、Word、PowerPoint、PDF
- API 整合：建立 MCP 服务器连接外部服务

### 个人应用

- 自订你的工作流程
- 让 Claude 配合你的习惯工作

## Security & Best Practices

[GitHub - travisvn/awesome-claude-skills: A curated list of awesome Claude Skills, resources, and tools for customizing Claude AI workflows — particularly Claude Code](https://github.com/travisvn/awesome-claude-skills?tab=readme-ov-file#-security--best-practices)

## Skills，MCP

### MCP 局限

随着时间推移，MCP 的局限性也开始显现。其中最显著的一点是对 token 的大量消耗：众所周知，GitHub 官方 MCP 本身就消耗了巨量上下文 token，而这种消耗量越大，大模型自身就越是没有发挥实际作用的空间。

可用 CLI 命令替代 MCP 操作，Skill 也知道这点

### MCP 和 Skills 区别

Skills = Instructions on HOW to do your workflows

MCP = Connections to WHAT you need access to

**Skills**：`教导 Claude 如何 执行特定任务的功能`。类似于提供详细的指导手册，让 Claude 学习并遵循你的工作流程。例如，使用公司特定的格式生成财务报告。这强调 Skills 的作用是 "**教学** "，帮助 Claude 掌握方法和步骤，从而处理结构化的、重复性的任务。

**MCP**：`连接 Claude 到它 需要 的外部资源的功能`。类似于为 Claude 提供数据 " 接口 "，让它能访问实时或外部信息。例如，从外部 API 获取实时股票价格。这强调 MCP 的作用是 "**连接**"，确保 Claude 能获取必要的数据或工具，而无需手动编写复杂的集成代码。

配图直观地对比了二者：

- 左侧（Skills）：标题为 "Teach Claude HOW to do it"（教 Claude 如何做），示例为公司格式的财务报告。
- 右侧（MCP）：标题为 "Connect to WHAT it needs"（连接到它需要的东西），示例为外部 API 的实时股票价格。
![image.png](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidian/202511112334573.png)
这也提供了一种 AI 开发合作方式：**Skills 提供 " 知识和方法 "，MCP 提供 " 数据和访问 "。** 在实际应用中，二者结合能让 Claude 更高效地处理复杂任务，例如在生成报告时，不仅知道格式（Skills），还能拉取最新数据（MCP）。这对开发者、企业和 AI 用户来说，具有实用价值，尤其在构建自定义智能体时，能简化集成外部系统的过程。

### 解决 MCP 上下文爆炸

solution to use MCP servers without context bloat:

<https://x.com/goon_nguyen/status/1987720058504982561>

## 创建 Skill

### 使用 skill-creator （推荐）

1. Enable the skill-creator skill in Claude
2. Ask Claude: "Use the skill-creator to help me build a skill for `[your task]`"
3. Answer the interactive questions about your workflow
4. Claude generates the complete skill structure for you

### 小结

Skills 的核心价值：**不是替代 CLAUDE.md，而是给 Claude 装上 " 工具箱 "。**

### 手动

1. 手动创建目录结构：

```shell
my-skill/
├── SKILL.md          # Main skill file with frontmatter
├── scripts/          # Optional executable scripts
│   └── helper.py
└── templates/        # Optional: Document templates
└── resources/        # Optional supporting files
    └── template.json

```

2. 创建**SKILL.md with frontmatter**:

```markdown
---
name: my-skill
description: Brief description for skill discovery (keep concise)
---

# Detailed Instructions

Claude will read these instructions when the skill is activated.

## Usage
Explain how to use this skill...

## Examples
Provide clear examples...
```

3. 添加 **executable scripts**（可选）：
	- Python, JavaScript, or other scripts Claude can execute
	- Reference them in your SKILL.md instructions
4. 本地测试
5. 分享

**skill.md 模板**：

```markdown
---
name: my-skill-name
description: A clear description of what this skill does and when to use it.
---

# My Skill Name

Detailed description of the skill's purpose and capabilities.

## When to Use This Skill

- Use case 1
- Use case 2
- Use case 3

## Instructions

[Detailed instructions for Claude on how to execute this skill]

## Examples

[Real-world examples showing the skill in action]
```

### Skill Best Practices

- **Keep descriptions concise** - The frontmatter `description` 用于技能发现
- **Use clear, actionable instructions** - 像人类合作者一样编写说明
- **Include examples** - 在你的 SKILL.md 中展示具体示例
- **Version your skills** - 使用 git 标签进行版本管理
- **Document dependencies** - 列出任何先决条件或所需的包
- **Test thoroughly** - 在不同场景下验证你的技能是否有效

其他：

- **脚本优先** 能用脚本处理的，别让 Claude 生成代码。
	- **确定性任务**(排序、格式转换、数据清洗)：写 Python/JS 脚本  
	- **创造性任务**(生成文案、代码架构设计)：让 Claude 发挥
- **保持专注** 一个 Skill 做一件事；别把 " 爬虫 + 清洗 + 分析 + 报表 + 邮件发送 " 塞一个 Skill，拆开，需要时 Claude 会自动组合多个 Skills。
- **多放实际例子** SKILL.md 里多放真实可运行的例子
- **附参考文档** 涉及特定库，把关键文档放进去

## Skills 使用

[Claude Skills 案例](Claude%20Skills%20案例.md)

## 安全使用 skills

### 安全 Tips

- ✅ 只用自己创建或官方的 Skills  
- ✅ 从 GitHub/插件安装前先看代码  
- ❌ 别用来路不明的 Skills  
- ❌ Skills 里别放 API 密钥

恶意 Skill 可能读取文件、执行危险命令、泄露信息。

**网上下载的 Skills，必须先检查 SKILL.md 和 scripts/所有代码。**

## 疑问

### Skill 能用 mcp? 安装和卸载 mcp?

### Skill 上下文会爆吗？

**不会。**

Skills 用渐进式加载 (Progressive Disclosure)：启动时只加载元数据 (~100 tokens)，需要时才读 SKILL.md(5k tokens 内)，脚本直接执行不占上下文。

你装 20 个 Skills，启动只占 2000 tokens。真正用到某个 Skill，才加载详细内容，用完释放。

Claude Code 的上下文窗口是 200k tokens，Skills 的渐进式加载让你可以装几十个 Skills 不用担心。

 **可以用/context 命令查看上下文使用情况，随时监控。**
