---
banner:
date_created: Monday, November 4th 2025, 11:45:00 pm
date_updated: Monday, November 4th 2025, 11:45:00 pm
title: Slash Commands 自定义命令指南
author: hacket
categories:
  - AI
category: ClaudeCode
tags: [AI, ClaudeCode, Commands, Slash-Commands, Automation]
toc: true
description: Claude Code 自定义 Slash Commands 完整指南 - 创建高效的工作流自动化命令
dg-publish: true
dg-enable-search: true
dg-show-local-graph: true
dg-show-toc: true
dg-show-file-tree: true
image-auto-upload: true
feed: show
format: list
aliases: [Slash Commands, 自定义命令, Commands]
linter-yaml-title-alias: Slash Commands 自定义命令指南
---

# Slash Commands 自定义命令指南

## 📖 概述

Slash Commands 是 Claude Code 的自定义命令系统，允许你创建可重用的工作流模板。通过 `/command-name` 的形式快速触发预定义的复杂任务。

### 核心价值

- ✅ **自动化重复任务** - 一键执行多步骤工作流
- ✅ **标准化流程** - 确保团队遵循最佳实践
- ✅ **提高效率** - 减少手动输入和配置
- ✅ **知识固化** - 将专家经验编码为可复用命令

### 与 Skills 的区别

| 特性 | Slash Commands | Skills |
|-----|----------------|--------|
| 触发方式 | `/command` 手动触发 | 自动匹配用户意图 |
| 适用场景 | 明确的工作流程 | 复杂的能力扩展 |
| 复杂度 | 简单的 prompt 模板 | 可包含脚本和资源 |
| 学习成本 | 低 | 中高 |

---

## 📂 目录结构

```
.claude/commands/
├── de-slop.md          # AI 生成代码清理命令
├── gh-commit.md        # 智能 Git 提交命令
└── your-command.md     # 自定义命令
```

每个命令是一个独立的 Markdown 文件。

---

## 🎯 项目内置命令

### 1. `/de-slop` - AI 代码清理命令

**用途**: 在提交 PR 前清理 AI 生成的冗余内容

**功能**:
- ✅ 扫描不必要的 Markdown 文件（NOTES.md, PLAN.md, TODO.md 等）
- ✅ 识别冗余注释（重复代码逻辑的注释）
- ✅ 检测 AI 风格的 TODO 注释
- ✅ 标记过度详细的 docstrings
- ✅ 发现 mock-heavy 的测试代码
- ✅ 识别未引用来源的假数据

**使用方法**:

```bash
# 与 base branch 对比
/de-slop

# 与特定 PR 对比
/de-slop 123
```

**工作流程**:

1. **上下文检查** - 确定对比基准（base branch 或 PR）
2. **扫描 Slop** - 检测 6 种常见问题模式
3. **展示发现** - 列出所有问题并编号
4. **交互式选择** - 用户选择要清理的项目
5. **执行清理** - 删除文件或清理代码
6. **生成总结** - 报告清理结果

**检测模式**:

```markdown
📋 文件级别:
- NOTES.md, PLAN.md, ARCHITECTURE.md
- THOUGHTS.md, IDEAS.md, SCRATCH.md
- TEMP.md, TODO.md

🚫 不会删除:
- README.md, CONTRIBUTING.md, CHANGELOG.md
- docs/**/*.md

💬 注释模式:
- 仅重述下一行代码的注释
- AI 风格 TODO: "# TODO: Add error handling"
- 代码注释中的 Emoji
- 简单函数的过长 docstrings

🧪 测试问题:
- 超过 3 个 @patch 装饰器
- 没有测试真实行为的测试

📊 假数据:
- 未引用来源的具体百分比
- "根据研究" 但无引用
```

**安全机制**:

- ✅ 始终先 dry run，用户确认后执行
- ✅ 疑似时标记而非删除
- ✅ 删除 >5 个文件或 >50 行时需要确认
- ✅ 永不删除重要文档（README、CONTRIBUTING 等）

**示例输出**:

```
🔍 Found 4 slop patterns

[1] NOTES.md (45 lines)
    → Delete: Unnecessary markdown

[2] src/user.py:23-28
    → Remove redundant comments:
    # Create user
    user = User()

[3] src/api.py:15-25
    → Simplify excessive docstring

[4] tests/test_user.py:50-70
    → Flag: Mock-heavy (5 mocks)

Enter numbers (1 2 4), range (1-4), 'all', or 'none': 1 2
```

---

### 2. `/gh-commit` (或 `/commit`) - 智能 Git 提交

**用途**: 自动分析变更并创建符合 Conventional Commits 规范的多个逻辑提交

**功能**:
- ✅ 分支安全检查（禁止直接提交到 main/master）
- ✅ 自动分析变更类型和范围
- ✅ 智能批处理相关变更
- ✅ 生成符合规范的提交信息
- ✅ 添加 AI 协作标记

**使用方法**:

```bash
# 自动分析并提交
/commit

# 带描述提示
/commit "add YAML support feature"
```

**工作流程**:

```mermaid
1. 安全检查
   ↓
2. 分析变更（按类型和范围分类）
   ↓
3. 批处理相关变更
   ↓
4. 逐批创建提交
   ↓
5. 生成总结和下一步建议
```

**提交类型**:

| 类型 | 说明 | 示例 |
|-----|------|------|
| `feat` | 新功能 | feat(yaml): add MD_YAML mode |
| `fix` | Bug 修复 | fix(validation): handle empty arrays |
| `docs` | 文档更新 | docs(README): update installation |
| `test` | 测试相关 | test(yaml): add validation tests |
| `refactor` | 重构代码 | refactor(auth): simplify token logic |
| `style` | 代码格式 | style: format with black |
| `perf` | 性能优化 | perf(query): add database index |
| `chore` | 构建/工具 | chore: update dependencies |
| `ci` | CI 配置 | ci: add Python 3.12 to matrix |

**批处理规则**:

```markdown
✅ 保持相关变更在一起:
- 实现 + 对应测试 → 一起提交
- 功能文件 + 功能文档 → 一起提交

❌ 分离不同关注点:
- 不混合无关代码
- 每个提交应该是原子的
- 测试独立时可以单独提交
```

**提交信息格式**:

```bash
type(scope): description

Optional body explaining why this change was made.

🤖 Generated with [Claude Code](https://claude.com/claude-code)
Co-Authored-By: Claude <noreply@anthropic.com>
```

**示例场景**:

假设你完成了 YAML 支持功能的开发：

```
📦 变更分析:
  - instructor/mode.py (新增 MD_YAML 枚举)
  - instructor/client_openai.py (YAML 处理逻辑)
  - instructor/yaml_handler.py (新文件)
  - tests/test_yaml.py (新文件)
  - tests/fixtures/yaml_samples.py (测试数据)
  - README.md (文档更新)
  - docs/concepts/yaml-mode.md (新文档)

📦 批次规划:
  Batch 1: Core implementation (3 files)
  Batch 2: Tests (2 files)
  Batch 3: Documentation (2 files)

✅ 创建 3 个提交:
  1. feat(yaml): add MD_YAML mode for YAML extraction
  2. test(yaml): add tests for MD_YAML mode
  3. docs(yaml): document MD_YAML usage
```

**安全特性**:

1. **分支保护**:
   ```bash
   ⚠️  You're on main/master!
   → Creating branch: feat/add-yaml-support
   ```

2. **智能文件选择**:
   ```bash
   # ✅ 精确添加
   git add file1.py file2.py file3.py

   # ❌ 永不使用
   git add .
   ```

3. **Pre-commit Hook 处理**:
   ```
   ⚠️  Pre-commit hook failed (formatting)

   Options:
   1. Auto-fix and amend current commit
   2. Create separate "style: format code" commit
   3. Skip and fix manually
   ```

**项目感知**:

命令会自动检查：
- `git log` 的最近提交，遵循项目风格
- `CLAUDE.md` 中的提交规范
- `CONTRIBUTING.md` 中的贡献指南
- `.gitmessage` 模板

---

## 🛠️ 创建自定义命令

### 基本结构

```markdown
# Command Title

Brief description of what this command does.

## Workflow

### 1. Step Name

**Description of step**

```bash
# Example commands
git status
```

Instructions for Claude...

### 2. Next Step

...

## Examples

Show example outputs...

## Usage

```bash
/your-command
/your-command arg1 arg2
```
```

### 最佳实践

1. **清晰的工作流** - 用编号步骤组织流程
2. **具体的指令** - 告诉 Claude 该做什么，而非如何思考
3. **安全检查** - 在危险操作前加入确认步骤
4. **示例输出** - 展示预期的输出格式
5. **错误处理** - 考虑异常情况的处理

### 命令模板

```markdown
# Your Command Name

One-line description.

## Workflow

### 1. Initial Check

```bash
# Commands to run
command1
command2
```

What Claude should do with the output...

### 2. Main Task

**Ask user:** "Clarifying question?"

Based on response:
- Option A: Do this
- Option B: Do that

### 3. Execute

```bash
# Actual execution commands
```

### 4. Summary

Report:
- What was done
- Results
- Next steps

## Examples

```
Example input/output...
```

## Safety

- Check X before doing Y
- Never do Z without confirmation
- Always validate A

## Usage

```bash
/your-command           # Basic usage
/your-command --option  # With options
```
```

---

## 📚 实际应用场景

### 场景 1: 准备 PR 提交

```bash
# Step 1: 清理 AI 生成的冗余内容
/de-slop

# Step 2: 创建规范的提交
/commit "implement user authentication"

# Step 3: 推送并创建 PR
git push -u origin feat/user-auth
gh pr create --fill
```

### 场景 2: 代码审查前准备

```bash
# 自动清理不应提交的文件
/de-slop

# 确认清理结果
git status

# 提交清理后的代码
/commit
```

### 场景 3: 多功能开发完成

```bash
# 智能批处理提交
/commit "add multiple features: auth, logging, config"

# 结果: 自动创建 3 个独立提交
# - feat(auth): implement JWT authentication
# - feat(logging): add structured logging
# - feat(config): support environment variables
```

---

## 🎯 命令组合策略

### 标准开发流程

```
开发 → /de-slop → /commit → Push → PR
```

### 大型重构流程

```
重构 → /de-slop → /commit → Code Review → /de-slop 再次清理 → /commit --amend
```

### 团队协作流程

```
1. Feature 开发完成
2. /de-slop 清理个人开发痕迹
3. /commit 创建规范提交
4. Push to feature branch
5. 创建 PR 等待审查
```

---

## 🔗 与其他系统集成

### 与 CLAUDE.md 配合

在 `CLAUDE.md` 中引用命令：

```markdown
## Git 工作流

开发完成后:
1. 运行 `/de-slop` 清理冗余代码
2. 运行 `/commit` 创建规范提交
3. 推送到远程分支
```

### 与 Hooks 配合

```json
{
  "hooks": {
    "before-commit": {
      "command": "/de-slop",
      "description": "Auto-clean before commit"
    }
  }
}
```

### 与 Skills 配合

Commands 处理流程性任务，Skills 处理能力性任务：

```
/commit (流程) → skill-creator (能力) → /de-slop (流程)
```

---

## 📖 命令开发指南

### 1. 识别可自动化的流程

寻找你重复执行的任务：
- Git 操作模式
- 代码审查检查清单
- 部署前检查
- 测试运行流程

### 2. 设计命令结构

```markdown
Input → Analysis → Action → Output → Next Steps
  ↓         ↓         ↓        ↓         ↓
用户请求  理解意图  执行操作  报告结果  建议后续
```

### 3. 测试和迭代

- 在真实项目中测试
- 收集团队反馈
- 逐步完善错误处理
- 添加更多安全检查

### 4. 文档化

- 清晰的使用说明
- 充足的示例
- 边界情况说明
- 安全注意事项

---

## ⚠️ 注意事项

### 命令设计原则

1. **幂等性** - 多次运行应该安全
2. **可预测** - 用户应该清楚会发生什么
3. **可撤销** - 提供撤销或恢复机制
4. **可观察** - 显示详细的执行过程

### 安全实践

```markdown
❌ 避免:
- 直接在 main 分支操作
- 无确认的删除操作
- git add . 全部添加
- 盲目执行外部命令

✅ 推荐:
- 操作前检查分支
- 危险操作需要确认
- 精确指定要添加的文件
- 显示命令将要执行的内容
```

### 调试技巧

当命令不按预期工作时：

1. **添加 echo 语句** - 显示中间变量
2. **分步执行** - 注释掉后续步骤
3. **检查返回值** - 确认命令成功执行
4. **查看 Claude 的理解** - 询问它对指令的解释

---

## 🎓 学习资源

### 官方文档
- [Slash Commands 官方指南](https://docs.anthropic.com/claude/docs/slash-commands)
- [Conventional Commits 规范](https://www.conventionalcommits.org/)

### 社区示例
- [awesome-claude-commands](https://github.com/example/awesome-claude-commands)
- 本项目的 `.claude/commands/` 目录

### 相关文档
- [[01-CLAUDE.md使用指南]] - 项目配置
- [[Claude Agent Skill]] - Skills 系统
- [[01-Hooks完全指南]] - Hooks 自动化

---

## 📝 总结

Slash Commands 是 Claude Code 工作流自动化的核心工具：

- ✅ **de-slop**: 清理 AI 生成的冗余代码
- ✅ **gh-commit**: 智能创建规范化的 Git 提交
- ✅ **自定义命令**: 固化你的最佳实践

**立即行动**:
1. 尝试运行 `/de-slop` 清理你的代码
2. 使用 `/commit` 创建你的下一个提交
3. 创建你的第一个自定义命令

---

**下一步**: [[Level-3-Extension-Systems/README]] | [[Claude Code Skills总结]]
