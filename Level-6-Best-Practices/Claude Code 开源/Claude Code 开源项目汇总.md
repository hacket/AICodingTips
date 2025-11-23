---
banner: 
date_created: Tuesday, July 22nd 2025, 1:04:56 am
date_updated: Sunday, November 23rd 2025, 1:32:07 pm
title: Claude Code 开源项目汇总
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
aliases: [Claude Code 开源]
linter-yaml-title-alias: Claude Code 开源
---

# Claude Code 开源

## 必备

- SuperClaude V3
- ccusage 查看 CC 使用
- ccundo

## awesome-claude-code

<https://github.com/hesreallyhim/awesome-claude-code>

## Claude Code 增强

将每个库的缩写，放到对应的 agents/commands/hooks 目录，方便调用，也方便管理

### 【cook】claude-code-cookbook

<https://github.com/foreveryh/claude-code-cookbook>

### 【sc】SuperClaude V3/V4

见 [SuperClaude-V3](SuperClaude-V3.md)、[SuperClaude-V4](SuperClaude-V4.md)

### ruvnet/claude-flow (截止 20250813 5.8k star)

<https://github.com/ruvnet/claude-flow>

### claude-code-templates (截止 20250910 5.7k star)

<https://www.aitmpl.com/>

<https://github.com/davila7/claude-code-templates>

**安装：**

```shell
npx claude-code-templates@latest
```

- 查看 Agents 使用
- Productivity Analytics
- Token Analytics
- Workflow Intelligence

## AI 版本控制

### yoyo

<https://www.runyoyo.com/>

提供更用户友好的快照和版本管理界面，适合需要直观操作的用户。

### ccundo

<https://github.com/RonitSachdev/ccundo>

用于跟踪和回滚 Claude Code 对文件的更改。命令如 `/CC_undo_list`（列出更改）、`/CC_undo_preview`（预览更改）和 `/CC_undo_undo`（回滚指定更改）让版本管理更方便。

## 连接其他模型

### cc-switch（推荐，有 UI 界面，配置简单）

[GitHub - farion1231/cc-switch: 一个用于管理和切换 Claude Code 和 Codex 不同供应商配置的桌面应用](https://github.com/farion1231/cc-switch)

### 其他

**1、claude-code-proxy：** 1rgs/claude-code-proxy(截止 20250811 1.9k star)
<https://github.com/1rgs/claude-code-proxy>

**2、cladue-code-router：** musistudio/claude-code-router (截止 20250811 11.9k star)
<https://github.com/musistudio/claude-code-router>

**3、kimi-cc：**
 kimi-cc【kimi 替代 Claude】
<https://github.com/LLM-Red-Team/kimi-cc>

## GUI

### ccusage

#### 基本使用

官方查看消耗，但过于笼统，不够直观，推荐使用 `ccusage` 工具来查看。

```shell
npm install -g ccusage
```

如果要查看自某天开始的消耗：

```shell
ccusage -s 20250721
```

![20250730233504628](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidian/20250816230219357.png)

如果要 `实时` 查看消耗：

```shell
ccusage blocks --live
# 或者
npx ccusage blocks --live
```

![20250816010750703](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidian/20250816230219364.png)

> Claude Pro / Max 订阅用户可以不用理会消耗，它是按月计费的，不是按使用量计费的。

**ccusage 其他常用指令**：

```shell
# 基础用法  
ccusage          # 显示每日报告（默认）  
ccusage daily    # 每日 token 使用量及费用  
ccusage monthly  # 月度汇总报告  
ccusage session  # 按会话统计用量  
ccusage blocks   # 5小时计费窗口数据  

# 实时监控  
ccusage blocks --live  # 实时用量仪表盘  

# 筛选与选项  
ccusage daily --since 20250525 --until 20250530  # 指定日期范围  
ccusage daily --json      # 输出 JSON 格式  
ccusage daily --breakdown # 按模型细分费用
```

#### 和 status line 配合

**和 status line 结合 (.claude/settings.json)：**

```json
{
  "statusLine": {
    "type": "command",
    "command": "bun x ccusage statusline",
  }
}
```

Extending ccusage to show more information as you use claude code: <https://gist.github.com/SomtoUgeh/4e74f7ad8ec7618116635b7f42e54034>

### Claude Code Web GUI

<https://github.com/binggg/Claude-Code-Web-GUI>

<https://binggg.github.io/Claude-Code-Web-GUI/>

浏览和查看您的 Claude Code 会话历史 - 完全在浏览器中运行，无需服务器

### opcode(原 claudia) 管理 Claude Code 的上下文和历史对话

<https://github.com/winfunc/opcode>

提前安装好：Rust、Bun、Git

```shell
# 检查Rust
rustc --version   
cargo --version  

# 检查Bun
bun --version  

# 检查Git
git --version
```

安装

```shell
# 克隆仓库  
git clone https://github.com/getAsterisk/claudia.git  
cd claudia  

# 安装前端依赖  
bun install  

# 构建应用程序  
bun run tauri build
```

注意要用 `bun run tauri build` 命令而不是 `bun run tauri dev` 命令，后者只是一次性的，你下次还得再运行一次才能打开。

安装成功后你就能得到这么一个 GUI 的工具。

### sniffly

Claude Code dashboard with usage stats, error analysis, and shareable feature

<https://github.com/chiphuyen/sniffly>

## 其他

### intellectronica/ruler

<https://github.com/intellectronica/ruler>

将 ai rules 应用到主流的 AI Agents

### claude-code-guide 【CC 入门教程】

<https://github.com/zebbern/claude-code-guide>

- Claude CLI 安装、配置、API Key 设置等全流程
- 详细讲解每个命令和参数，包含 REPL、One-Shot、Session、Config 等模式
 - MCP 工具集成和权限系统实操，支持自动化、CI/CD、项目协作等高级用法
- 内置健康检查、安全建议、常见问题排查，适合日常开发和团队协作
 - 适配多平台，支持 NPM，brew，Docker，WSL 等多种安装方式

### 移动端 happy coding

<https://github.com/slopus/happy>

可以在手机上连上你桌面端的 claude code，并在移动端 happy coding

<https://github.com/mylukin/ccanywhere>
