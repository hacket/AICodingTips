# Claude Code 学习导航

> 一份循序渐进的 Claude Code 中文学习指南

## 为什么做这个项目

Claude Code 是 Anthropic 推出的强大 AI 编程助手,但官方文档都是英文的,对中文开发者不太友好。这个项目整理了一套完整的中文学习路径,帮你快速上手并深入掌握 Claude Code。

## 项目结构

```
ClaudeCode/
├── 01-Core/              # 核心功能 - 从这里开始
├── 02-Extensions/        # 扩展系统 - Commands、Skills、MCP、Hooks
└── 03-Best-Practices/    # 最佳实践 - 使用技巧和开源项目
```

---

## 📖 学习路径

### 🚀 第一步:核心功能 ([01-Core](01-Core/))

**适合人群**: 所有人,特别是刚接触 Claude Code 的同学

从安装开始,学会基本的使用方法:
- [安装与配置](01-Core/01-安装与配置.md) - 如何安装和初始配置
- [基本用法](01-Core/02-基本用法.md) - 最常用的功能和命令
- [常用命令参考](01-Core/03-常用命令参考.md) - 命令速查手册
- [工作流实践](01-Core/04-工作流实践.md) - 日常开发中如何使用
- [CLAUDE.md 使用指南](01-Core/05-CLAUDE.md使用指南.md) - 项目配置文件详解
- [使用其他大模型](01-Core/06-使用其他大模型.md) - 配置使用 GPT、Gemini 等
- [Android 编码规范](01-Core/07-Android编码规范.md) - Android 项目配置示例

### ⚡ 第二步:扩展系统 ([02-Extensions](02-Extensions/))

**适合人群**: 想深入使用 Claude Code 的开发者

这部分是 Claude Code 的精华,学会这些能大幅提升效率:

#### 🛠️ 四大扩展工具

1. **[Commands](02-Extensions/COMMANDS.md)** - 120+ 个实用命令
   - `/think-ultra` - 深度思考分析
   - `/kiro:spec` - 需求到实现的完整流程
   - `/gh:review-pr` - 自动化 PR 审查
   - 更多命令详见文档...

2. **[Skills](02-Extensions/SKILLS.md)** - 19 个专业技能包
   - `docx/pdf/xlsx/pptx` - 文档处理
   - `algorithmic-art` - 算法艺术创作
   - `deep-reading-analyst` - 深度阅读分析
   - 更多 Skills 详见文档...

3. **MCP 服务器** - 连接外部服务
   - [MCP 基础与使用](02-Extensions/03-MCP基础与使用.md)
   - 集成 GitHub、数据库、API 等

4. **Hooks 和 Sub-Agents** - 自动化和智能化
   - [Sub-Agents 使用指南](02-Extensions/02-Sub-Agents使用指南.md)
   - [Hooks 完全指南](02-Extensions/04-Hooks完全指南.md)

#### 📚 深入学习

- [扩展系统概述](02-Extensions/01-扩展系统概述.md) - 整体了解扩展生态
- [Skills 案例](02-Extensions/skills/) - 实际使用案例

### 💡 第三步:最佳实践 ([03-Best-Practices](03-Best-Practices/))

**适合人群**: 想用好 Claude Code 的所有人

看看官方推荐和其他开发者的经验:
- [官方最佳实践](03-Best-Practices/01-官方最佳实践.md) - Anthropic 官方建议
- [个人使用总结](03-Best-Practices/02-个人使用总结.md) - 实战经验分享
- [使用技巧](03-Best-Practices/03-使用技巧.md) - 提效小技巧
- [开源项目](03-Best-Practices/04-开源项目/) - SuperClaude 等优秀配置

---

## 🎯 学习建议

**如果你是新手**:
1. 先看 `01-Core` 的安装和基本用法
2. 试着在实际项目中用一用
3. 遇到问题翻翻 `03-Best-Practices` 的技巧

**如果你有经验**:
1. 直接跳到 `02-Extensions` 学习 Commands 和 Skills
2. 配置自己的 MCP 服务器
3. 看看 `03-Best-Practices` 里的开源项目,吸收别人的配置

**如果你是团队使用**:
1. 参考 `01-Core` 里的 CLAUDE.md 配置规范
2. 用 `02-Extensions` 的 Commands 统一团队工作流
3. 研究 Hooks 实现团队级自动化

---

## 🔗 相关资源

### 官方文档
- [Claude Code 官方文档](https://docs.anthropic.com/zh-CN/docs/claude-code/overview)
- [Claude Code GitHub](https://github.com/anthropics/claude-code)
- [Anthropic 课程](https://anthropic.skilljar.com/)

### 社区资源
- [My Claude Code Learning Path](https://x.com/dani_avila7/status/1983331447571124382)
- 更多资源持续更新中...

---

## 📝 贡献

发现错误或有更好的建议?欢迎提 Issue 或 PR!

## 许可

MIT License
