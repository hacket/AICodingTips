---
banner: 
date_created: Thursday, July 31st 2025, 11:52:32 pm
date_updated: Sunday, October 19th 2025, 10:02:50 am
title: 02-Claude Code Hooks钩子
author: hacket
categories:
  - AI
category: ClaudeCode
tags: [AI, ClaudeCode, VibeCoding]
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
aliases: [Claude Code Hooks]
linter-yaml-title-alias: Claude Code Hooks
---

# Claude Code Hooks

## Hooks 介绍？

Claude Code Hooks 是用户定义的 shell 命令，在 Claude Code 生命周期的各个点执行。Hooks 提供对 Claude Code 行为的确定性控制，确保某些操作总是发生，而不是依赖 LLM 选择运行它们。

一些 hooks 的典型用例包括：

- **Notifications**：自定义当 Claude Code 等待你输入或授权时的通知方式。
- **Automatic formatting**：每次文件编辑后自动执行 prettier（用于 .ts 文件）、gofmt（用于 .go 文件）等。
- **Logging**：记录和统计所有执行的命令，以满足合规性或调试需要。
- **Feedback**：当 Claude Code 生成不符合你代码规范的代码时，提供自动反馈。
- **Custom permissions**：阻止对生产文件或敏感目录的修改。

## Hooks 基础

### 配置

#### settings.json 配置文件

Claude Code 钩子在您的 [settings.json设置文件](https://docs.anthropic.com/zh-CN/docs/claude-code/settings) 中配置：

- `~/.claude/settings.json` - 用户设置
- `.claude/settings.json` - 项目设置
- `.claude/settings.local.json` - 本地项目设置（不提交）
- 企业管理策略设置

#### structure 结构

钩子按 `matchers` 组织，每个 `matchers` 可以有多个钩子：

```json
{
  "hooks": {
    "EventName": [
      {
        "matcher": "ToolPattern",
        "hooks": [
          {
            "type": "command",
            "command": "your-command-here"
          }
        ]
      }
    ]
  }
}
```

- **matcher**: 匹配工具名称的模式，区分大小写（仅适用于 `PreToolUse` 和 `PostToolUse`）
	- 简单字符串精确匹配：`Write` 仅匹配 Write 工具
	- 支持正则表达式：`Edit|Write` 或 `Notebook.*`
	- 使用 `*` 匹配所有工具。您也可以使用空字符串（`""`）或留空 `matcher`。
- **hooks**: 当模式匹配时要执行的命令数组
	- `type`: 目前仅支持 `"command"`
	- `command`: 要执行的 bash 命令（可以使用 `$CLAUDE_PROJECT_DIR` 环境变量）
	- `timeout`: （可选）命令应运行多长时间（以秒为单位），超时后 取消该特定命令。

对于像 `UserPromptSubmit`、`Notification`、`Stop` 和 `SubagentStop` 这样不使用 `matcher` 的事件，您可以省略 `matcher` 字段：

```json
{
  "hooks": {
    "UserPromptSubmit": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "/path/to/prompt-validator.py"
          }
        ]
      }
    ]
  }
}
```

#### Project-Specific Hook Scripts 项目特定 Hook 脚本

您可以使用环境变量 `CLAUDE_PROJECT_DIR`（仅在 Claude Code 生成钩子命令时可用）来引用存储在项目中的脚本， 确保无论 Claude 的当前目录如何，它们都能正常工作：

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "$CLAUDE_PROJECT_DIR/.claude/hooks/check-style.sh"
          }
        ]
      }
    ]
  }
}
```

### Hook Events

Claude Code 提供多个 hook 事件，它们在工作流的不同阶段触发：

- **PreToolUse**：在工具调用之前运行（可以阻止调用）
- **PostToolUse**：在工具调用完成后运行
- **Notification**：当 Claude Code 发出通知时运行
- **UserPromptSubmit**：
- **Stop**：Claude Code 响应结束时运行
- **Subagent Stop**：subagent 任务完成时运行
- **PreCompat**：
- **SessionStart**：

#### PreToolUse function call 之前执行

在 Claude 创建 `tool parameters` 之后、处理 `tool call` 之前运行。

> 在创建工具参数后、处理工具调用前运行。可以匹配 Task（代理任务）、Bash（Shell 命令）、Read（文件读取）、Edit/MultiEdit（文件编辑）等工具。

**常见 matchers：**
- `Task` - 子代理任务（参见 [子代理文档](https://docs.anthropic.com/zh-CN/docs/claude-code/sub-agents)）
- `Bash` - Shell 命令
- `Glob` - 文件模式匹配
- `Grep` - 内容搜索
- `Read` - 文件读取
- `Edit`、`MultiEdit` - 文件编辑
- `Write` - 文件写入
- `WebFetch`、`WebSearch` - Web 操作

**PreToolUse 示例：**

```json
"PreToolUse": [
  {
    "matcher": "Read",
    "hooks": [
      {
        "type": "command",
        "command": "node /home/hooks/read_hook.ts"
      }
    ]
  }
]
```

在这个例子中：

- 每當 Claude 嘗試使用 Read 工具時，就會先執行指定的指令 `node read_hook. ts`
- 你的命令會從標準輸入（stdin）接收到工具調用的 JSON 詳細資料
- 然後你可以根據這些資訊做出兩種決策：
	- 允許：回傳 exit code 0，Claude 將正常繼續執行工具
	- 阻擋：回傳 exit code 2，Claude 將中止該操作，並顯示 stderr 作為錯誤提示

#### PostToolUse function call 之后执行

在工具成功完成后立即运行。识别与 `PreToolUse` 相同的 matchers 值。

> 在工具成功完成后立即运行。识别与 PreToolUse 相同的匹配器值。

是在 Claude 执行工具之后调用，因为无法阻止操作，但你可以进行：

- 文档格式化
- 对 Claude 回传附加信息或后处理结果

```json
"PostToolUse": [
  {
    "matcher": "Write|Edit|MultiEdit",
    "hooks": [
      {
        "type": "command", 
        "command": "node /home/hooks/edit_hook.ts"
      }
    ]
  }
]
```

在这个例子中：

- 当 Claude 执行写入或编辑后，就会自动执行 `edit_hook.ts`
- 这个脚本可以读取 Claude 刚刚操作的内容，例如格式、文件名、变更差异等，并进行额外后处理

#### Notification

当 Claude Code 发送通知时运行。通知在以下情况下发送：

1. Claude 需要您的权限来使用工具。例如："Claude 需要您的权限来使用 Bash"
2. 提示输入已空闲至少 60 秒。"Claude 正在等待您的输入 "

#### UserPromptSubmit

当用户提交提示时、Claude 处理之前运行。这允许您根据提示/对话添加额外的上下文、验证提示或阻止某些类型的提示。

#### Stop

当主 Claude Code 代理完成响应时运行。如果停止是由于用户中断而发生的，则不会运行。

#### SubagentStop

当 Claude Code 子代理（Task 工具调用）完成响应时运行。

#### PreCompact

在 Claude Code 即将运行压缩操作之前运行。

**匹配器：**

- `manual` - 从 `/compact` 调用
- `auto` - 从自动压缩调用（由于上下文窗口已满）

#### SessionStart

当 Claude Code 启动新会话或恢复现有会话时运行（目前确实会在底层启动新会话）。对于加载开发上下文（如现有问题或代码库的最近更改）很有用。

**匹配器：**

- `startup` - 从启动调用
- `resume` - 从 `--resume`、`--continue` 或 `/resume` 调用
- `clear` - 从 `/clear` 调用

## QuickStart

本快速开始示例将添加一个 hook，用于记录 Claude Code 执行的 shell 命令。

**0、Prerequisites：** 安装 jq，用于命令行中处理 JSON。

```shell
# Mac
brew install jq

# Windows(需要先安装Chocolatey)
choco install jq

# 测试
jq --version
```

**1、打开 hooks 配置**
运行 `/hooks` slash 命令，选择 `PreToolUse` hook 事件。
![image.png](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidian/20250805003012787.png)

![image.png](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidian/20250805003053004.png)

`PreToolUse` hooks 会在工具调用之前运行，并可阻止这些调用，同时给 Claude 提供修改建议。

**2、添加 matcher**
选择 **+ Add new matcher…**，仅在 Bash 工具调用时运行你的 hook。输入 `Bash` 作为 matcher。
![image.png](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidian/20250805003239494.png)
你也可以使用 `*` 来匹配所有工具。

**3、添加 hook**
选择 **+ Add new hook…** 并输入以下命令：

```shell
jq -r '"(.tool_input.command) - (.tool_input.description // "No description")"' >> ~/.claude/bash-command-log.txt
```

![image.png](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidian/20250805003427554.png)

**4、保存你的配置**
在 storage location 处选择 **User settings**，因为你是将日志写入主目录。此 hook 将适用于所有项目，而不仅仅是当前项目。
然后按下 `Esc`，返回到 REPL。你的 hook 已经注册成功！

```json
{
  "permissions": {
    "defaultMode": "bypassPermissions"
  },
  "hooks": {
    "stop": [
      {
        "type": "command",
        "command": "C:\\Python\\python.exe D:\\ai\\AIDemos\\CCHooks\\notify.py"
      }
    ],
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "jq -r '\"(.tool_input.command) - (.tool_input.description // \"No description\")\"' >> ~/.claude/bash-command-log.txt"
          }
        ]
      }
    ]
  }
}
```

**5、验证你的 hook**
再次运行 `/hooks`，或查看 `~/.claude/settings.json`，你会看到如下配置：

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "jq -r '"\(.tool_input.command) - \(.tool_input.description // "No description")"' >> ~/.claude/bash-command-log.txt"
          }
        ]
      }
    ]
  }
}
```

**6、测试你的 hook**
请求 Claude 执行一个简单命令，如 `ls`，然后查看日志文件：

```shell
cat ~/.claude/bash-command-log.txt
```

## 高级用户的进阶技巧

### 动态环境变量

Claude Code 提供了你可以在 hooks 中使用的上下文感知变量：

- `$CLAUDE_FILE_PATHS` - 正在修改的文件  
- `$CLAUDE_TOOL_INPUT` - 完整工具参数的 JSON 格式  
- `$CLAUDE_NOTIFICATION` - 通知消息内容

### JSON 驱动的控制流

对于复杂的工作流程，hooks 可以返回结构化 JSON 来控制 Claude 的行为：

```shell
#!/bin/bash
# analyze_code.sh
analysis_result=$(eslint $CLAUDE_FILE_PATHS --format json)
if [ $? -ne 0 ]; then
  echo '{
    "decision": "block",
    "reason": "Code contains linting errors. Please fix them first.",
    "continue": false
  }'
  exit 0
fi
```

### 并行处理能力

所有匹配的 hooks 并行运行，允许你同时执行多个检查，而不会减慢你的工作流程。

### Monorepo 革命

该功能还解决了 monorepo 挑战，其中需要根据包含更改的目录运行不同的 linter 和工具。

```shell
[hooks](hooks.md)
event = "PostToolUse"
[hooks.matcher]
tool_name = "edit_file"
command = """
for file in $CLAUDE_FILE_PATHS; do
  case $file in
    frontend/*.ts) prettier --write "$file" ;;
    backend/*.go) gofmt -w "$file" ;;
    docs/*.md) markdownlint --fix "$file" ;;
  esac
done
"""
```

### 安全性：强大的力量带来巨大的责任

Claude Code hooks 会在你的系统上自动执行任意 shell 命令。通过使用 hooks，你承认你对你配置的命令负全部责任。

直接编辑设置文件中的 hooks 不会立即生效。Claude Code 在启动时捕获 hooks 的快照，并在整个会话中使用此快照。这防止恶意修改影响你当前的工作。

### 与现有工作流程的集成

#### Pre-commit Hook 集成

所有这些的真正魔力是将这些任务添加到 pre-commit hook 中。我推荐 pre-commit python 包。

```yaml
# .pre-commit-config.yaml
repos:
  - repo: local
    hooks:
      - id: claude-code-checks
        name: Claude Code Quality Checks
        entry: claude-code-check
        language: system
        files: '\.(py|js|ts)$'
```

#### CI/CD 流水线增强

Hooks 可以触发你的持续集成工作流程：

```yaml
[hooks](hooks.md)
event = "Stop"
command = """
if [ -n "$(git status --porcelain)" ]; then
  git add -A
  git commit -m "Auto-commit: Claude Code changes"
  git push origin feature/$(date +%Y%m%d-%H%M%S)
  gh pr create --title "Claude Code: Automated improvements" --body "Automated PR created by Claude Code hooks"
fi
"""
```

### 热门社区 Hooks

从 awesome-claude-code 仓库中，开发者们分享了用于以下功能的 hooks：

- 自动 GitHub 问题创建和解决  
- 智能提交消息生成  
- 跨平台构建自动化  
- 文档同步  
- 测试覆盖率强制执行

## CC Hooks 坑？

- 默认不是输出到终端，需要按 Ctrl+R
- 输入是标准流输入

## CC Hooks 使用场景

### 防止 Claude Code 敷衍回复

用 pre prompt submit hook 阻止他说一些话；用于防止 AI 助手使用过于简单或讨好的语言回应用户。脚本会检测助手是否使用了类似 `"你是对的"、"You're right"` 等敷衍性表达，如果发现，会自动插入系统提示，要求助手提供更深入的技术分析。

<https://gist.github.com/ljw1004/34b58090c16ee6d5e6f13fce07463a31>

### 修改后代码格式化

在编辑后自动格式化 TypeScript 文件：

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit|MultiEdit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "jq -r '.tool_input.file_path' | { read file_path; if echo "$file_path" | grep -q '\.ts$'; then npx prettier --write "$file_path"; fi; }"
          }
        ]
      }
    ]
  }
}
```

### 当 Claude 需要输入时，触发桌面通知

```json
{
  "hooks": {
    "Notification": [
      {
        "matcher": "",
        "hooks": [
          {
            "type": "command",
            "command": "notify-send 'Claude Code' 'Awaiting your input'"
          }
        ]
      }
    ]
  }
}
```

### 自动化测试

代码变更后触发单元测试或整体测试

### 存取控制

阻止 Claude Code 读取或编辑敏感文档。

假設使用者輸入 "read a.env file"，但我們不想要 Claude 去讀取。

```json

  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Edit|MultiEdit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "python3 -c "import json, sys; data=json.load(sys.stdin); path=data.get('tool_input',{}).get('file_path',''); sys.exit(2 if any(p in path for p in ['.env', 'package-lock.json', '.git/']) else 0)""
          }
        ]
      }
    ]
  }
}
```

### 程序质量检查

执行 linter 或 type checker，并将错误反馈给 Claude Code

- 任务完成后，发消息

## 开源

### zxdxjtu/claudecode-rule2hook

<https://github.com/zxdxjtu/claudecode-rule2hook>

根据自然语言生成 hook

### awesome-claude-code#hooks

<https://github.com/hesreallyhim/awesome-claude-code?tab=readme-ov-file#hooks>

### johnlindquist/claude-hooks

<https://github.com/johnlindquist/claude-hooks>

**安装 claude-hooks：**

```shell
npm install -g claude-hooks

# 需要安装bun
curl -fsSL https://bun.sh/install | bash

claude-hooks
```

![image.png](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidian/20250806003148771.png)

**生成的文件：**

```json
.claude/
├── settings.json
└── hooks/
    ├── index.ts
    ├── lib.ts
    └── session.ts
```

**自定义 hook 逻辑：**
在 `.claude/hooks/index.ts` 中自定义逻辑

### claude-code-hooks-mastery(截止 2025 年 8 月 8 日 800star)

<https://github.com/disler/claude-code-hooks-mastery>

## Ref

- Claude Code hooks <https://docs.anthropic.com/en/docs/claude-code/hooks-guide>
- Hooks reference <https://docs.anthropic.com/en/docs/claude-code/hooks>
