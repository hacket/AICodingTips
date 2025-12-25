# AI 编程实战指南

> 分享 AI 辅助编程的实用技巧和最佳实践

## 📚 项目内容

这个仓库收集了 AI 编程工具的学习笔记和实战经验,目前主要包含:

### 🤖 [Claude Code 完整教程](ClaudeCode/)

一套系统的 Claude Code 中文学习路径,从入门到精通:
- **核心功能** - 安装配置、基本用法、命令参考
- **扩展系统** - Commands、Skills、MCP、Hooks
- **最佳实践** - 使用技巧、开源项目

[👉 开始学习 Claude Code](ClaudeCode/)

---

## 🛠️ 可用工具速览

### Commands - 120+ 个实用命令

已配置在 `.claude/commands/` 目录下,主要分类:

**核心思维工具 (6 个)**
- `think-ultra` - 超深度思考分析
- `think-harder` - 增强分析思维
- `eureka` - 技术突破捕获
- `reflection` - 代码优化反思
- `reflection-harder` - 全面会话分析
- `rule2hook` - 规则转 Hooks 配置

**Kiro 开发框架 (5 个)**
- `kiro:spec` - 完整功能规范
- `kiro:design` - 功能设计文档
- `kiro:task` - 实施任务列表
- `kiro:execute` - 执行具体任务
- `kiro:vibe` - 快速开发帮助

**SC/Serena AI 辅助系统 (25+ 个)**
```
implement, design, test, build, save, load, index
analyze, improve, cleanup, document, explain
brainstorm, workflow, estimate, troubleshoot, reflect
help, select-tool, spec-panel, git, task, spawn
```

**Cook 通用工具集 (40+ 个)**
- PR 管理: `pr-create`, `pr-review`, `pr-list`, `pr-feedback` 等
- 代码质量: `refactor`, `explain-code`, `fix-error`, `smart-review` 等
- 依赖更新: `update-node-deps`, `update-flutter-deps`, `update-rust-deps` 等
- 规划思维: `plan`, `show-plan`, `task`, `spec`, `ultrathink` 等
- 协作角色: `multi-role`, `role`, `role-debate`, `team-collab` 等
- 其他工具: `screenshot`, `context7`, `search-gemini`, `check-fact` 等

**GitHub 集成 (3 个)**
- `gh:review-pr` - PR 代码审查
- `gh:fix-issue` - 修复 GitHub Issue
- `gh:gh-commit` - GitHub 提交辅助

**BMad 业务敏捷 (30+ 个)**
- 10 个专家角色: analyst, architect, dev, pm, po, qa, sm, ux-expert 等
- 20+ 任务流程: advanced-elicitation, create-doc, qa-gate, test-design 等

**其他工具**
- `cc:create-command` - 创建自定义命令
- `de-slop` - PR 清理工具

📖 [查看 Commands 完整文档](ClaudeCode/02-Extensions/COMMANDS.md)

### Skills - 19 个专业技能包

已配置在 `.claude/skills/` 目录下,主要分类:

**📄 文档处理 (5 个)**
- `docx` - Word 文档处理
- `pdf` - PDF 文档操作
- `xlsx` - Excel 表格处理
- `pptx` - PowerPoint 演示
- `pdf-processing-pro` - 高级 PDF 处理

**🎨 艺术设计 (3 个)**
- `algorithmic-art` - 算法艺术创作
- `canvas-design` - 视觉设计
- `slack-gif-creator` - Slack 动画制作

**🌐 前端 Web (3 个)**
- `artifacts-builder` - 复杂 Web 应用构建
- `theme-factory` - 主题定制
- `webapp-testing` - Web 自动化测试

**🔍 内容分析 (3 个)**
- `deep-reading-analyst` - 深度阅读分析
- `mcp-builder` - MCP 服务开发
- `internal-comms` - 内部沟通文档

**⚙️ 开发工具 (3 个)**
- `skill-creator` - Skill 开发
- `video-downloader` - 视频下载
- `template-skill` - Skill 模板

**🎥 媒体处理 (2 个)**
- `brand-guidelines` - 品牌规范
- `source-tracing` - 源码追踪

📖 [查看 Skills 完整文档](ClaudeCode/02-Extensions/SKILLS.md)

---

## 🚀 快速开始

### 1. Clone 项目

```bash
git clone <your-repo-url>
cd AICodingTips
```

### 2. 浏览学习内容

```bash
# 查看 Claude Code 教程
cd ClaudeCode

# 教程包含:
# - 01-Core/ 核心功能和基本用法
# - 02-Extensions/ 扩展系统(Commands/Skills/MCP/Hooks)
# - 03-Best-Practices/ 最佳实践和技巧
```

### 3. 使用配置好的工具

项目已经配置了 120+ 个 Commands 和 19 个 Skills,可以直接在 Claude Code 中使用:

```bash
# 使用命令示例
/think-ultra 如何优化数据库查询性能
/kiro:spec 用户认证系统
/gh:review-pr 123

# 使用技能示例
使用 docx skill 创建技术文档
使用 deep-reading-analyst skill 分析这篇论文
使用 algorithmic-art skill 创建流场可视化
```

---

## 📖 学习路径

### 新手入门

1. 阅读 [Claude Code 安装与配置](ClaudeCode/01-Core/01-安装与配置.md)
2. 学习 [基本用法](ClaudeCode/01-Core/02-基本用法.md)
3. 尝试使用几个常用命令,比如 `/think-harder`、`/kiro:vibe`
4. 查看 [使用技巧](ClaudeCode/03-Best-Practices/03-使用技巧.md)

### 进阶使用

1. 学习 [扩展系统概述](ClaudeCode/02-Extensions/01-扩展系统概述.md)
2. 深入研究 [Commands 文档](ClaudeCode/02-Extensions/COMMANDS.md)
3. 探索 [Skills 文档](ClaudeCode/02-Extensions/SKILLS.md)
4. 配置自己的 [MCP 服务器](ClaudeCode/02-Extensions/03-MCP基础与使用.md)
5. 设置 [Hooks](ClaudeCode/02-Extensions/04-Hooks完全指南.md) 实现自动化

### 高级实践

1. 参考 [开源项目](ClaudeCode/03-Best-Practices/04-开源项目/) 的配置
2. 使用 `skill-creator` 创建自定义 Skills
3. 使用 `cc:create-command` 创建自定义 Commands
4. 分享你的使用经验和最佳实践

---

## 🤝 贡献

欢迎贡献你的经验和技巧!

- 发现错误? 提 Issue
- 有更好的实践? 提 PR
- 想分享经验? 添加到 Best Practices

---

## 📝 许可

MIT License

---

## 🔗 相关资源

- [Claude Code 官方文档](https://docs.anthropic.com/zh-CN/docs/claude-code/overview)
- [Claude Code GitHub](https://github.com/anthropics/claude-code)
- [Anthropic 课程](https://anthropic.skilljar.com/)

---

**最后更新**: 2025-12-26
