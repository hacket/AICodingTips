---
banner: 
date_created: Wednesday, August 6th 2025, 12:43:15 am
date_updated: Tuesday, August 12th 2025, 12:49:09 am
title: Claude Code MCP
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
aliases: [Claude Code MCP]
linter-yaml-title-alias: Claude Code MCP
---

# Claude Code MCP

## MCP 服务器基础

官方文档：<https://docs.anthropic.com/zh-CN/docs/claude-code/mcp>

### 配置 MCP 服务器

- 添加 MCP `stdio` 服务器

```shell
# 基本语法
claude mcp add <name> <command> [args…]

# 示例：添加本地服务器
claude mcp add my-server -e API_KEY=123 -- /path/to/server arg1 arg2
```

- 添加 MCP `SSE` 服务器

```shell
# 基本语法
claude mcp add --transport sse <name> <url>

# 示例：添加 SSE 服务器
claude mcp add --transport sse sse-server https://example.com/sse-endpoint

# 示例：添加带有自定义标头的 SSE 服务器
claude mcp add --transport sse api-server https://api.example.com/mcp -e X-API-Key=your-key
```

- 添加 MCP `HTTP` 服务器名称

```shell
# 基本语法
claude mcp add --transport http <name> <url>

# 示例：添加可流式传输的 HTTP 服务器
claude mcp add --transport http http-server https://example.com/mcp

# 示例：添加带有身份验证标头的 HTTP 服务器
claude mcp add --transport http secure-server https://api.example.com/mcp -e Authorization="Bearer your-token"
```

- 使用 `-s` 或 `--scope` 标志指定配置存储位置：
	- `local`（默认）：仅在当前项目中对您可用（在旧版本中称为 `project`）
	- `project`：通过 `.mcp.json` 文件与项目中的每个人共享
	- `user`：在所有项目中对您可用（在旧版本中称为 `global`）
- 使用 `-e` 或 `--env` 标志设置环境变量（例如，`-e KEY=value`）
- 使用 `MCP_TIMEOUT` 环境变量配置 MCP 服务器启动超时（例如，`MCP_TIMEOUT=10000 claude` 设置 10 秒超时）
- 随时使用 Claude Code 中的 `/mcp` 命令检查 MCP 服务器状态
- MCP 遵循客户端 - 服务器架构，其中 Claude Code（客户端）可以连接到多个专用服务器
- Claude Code 支持 SSE（服务器发送事件）和可流式传输的 HTTP 服务器进行实时通信
- 使用 `/mcp` 与需要 OAuth 2.0 身份验证的远程服务器进行身份验证

**其他：**
安装 MCP 真的烦得要死，Claude mcp 命令一直无法正确安装，我直接打开.claude.json 自己填上去

### 管理您的 MCP 服务器

```shell
# 列出所有已配置的服务器
claude mcp list

# 获取特定服务器的详细信息
claude mcp get my-server

# 删除服务器
claude mcp remove my-server

# 使用 /mcp 命令来查看 MCP 服务器相关信息：
```

### MCP 服务器作用域

MCP 服务器可以在三个不同的作用域级别进行配置，每个级别都有不同的用途来管理服务器可访问性和共享。了解这些作用域有助于您确定为特定需求配置服务器的最佳方式。

#### 作用域层次结构和优先级

MCP 服务器配置遵循清晰的优先级层次结构。当同名服务器存在于多个作用域时，系统通过优先考虑 `本地作用域服务器`，然后是 `项目作用域服务器`，最后是 `用户作用域服务器` 来解决冲突。这种设计确保个人配置可以在需要时覆盖共享配置。

#### 本地作用域

本地作用域服务器代表默认配置级别，存储在您的项目特定用户设置中。这些服务器对您保持私有，仅在当前项目目录中工作时可访问。此作用域非常适合个人开发服务器、实验性配置或包含不应共享的敏感凭据的服务器。

```shell
# 添加本地作用域服务器（默认）
claude mcp add my-private-server /path/to/server

# 显式指定本地作用域
claude mcp add my-private-server -s local /path/to/server
```

#### 项目作用域

项目作用域服务器通过将配置存储在项目根目录的 `.mcp.json` 文件中来实现团队协作。此文件设计为检入版本控制，确保所有团队成员都能访问相同的 MCP 工具和服务。当您添加项目作用域服务器时，Claude Code 会自动创建或更新此文件，使用适当的配置结构。

```shell
# 添加项目作用域服务器
claude mcp add shared-server -s project /path/to/server
```

生成的 `.mcp.json` 文件遵循标准化格式：

```json
{
  "mcpServers": {
    "shared-server": {
      "command": "/path/to/server",
      "args": [],
      "env": {}
    }
  }
}
```

出于安全原因，Claude Code 在使用来自 `.mcp.json` 文件的项目作用域服务器之前会提示批准。如果您需要重置这些批准选择，请使用 `claude mcp reset-project-choices` 命令。

#### 用户作用域

用户作用域服务器提供跨项目可访问性，使它们在您机器上的所有项目中可用，同时对您的用户帐户保持私有。此作用域适用于个人实用程序服务器、开发工具或您在不同项目中经常使用的服务。

```shell
# 添加用户服务器
claude mcp add my-user-server -s user /path/to/server
```

#### 选择正确的作用域

根据以下条件选择您的作用域：

- **本地作用域**：个人服务器、实验性配置或特定于一个项目的敏感凭据
- **项目作用域**：团队共享服务器、项目特定工具或协作所需的服务
- **用户作用域**：多个项目中需要的个人实用程序、开发工具或经常使用的服务

### 与远程 MCP 服务器进行身份验证

许多远程 MCP 服务器需要身份验证。Claude Code 支持 OAuth 2.0 身份验证流程，以安全连接到这些服务器。

- **添加需要身份验证的远程服务器**

```shell
# 添加需要 OAuth 的 SSE 或 HTTP 服务器
claude mcp add --transport sse github-server https://api.github.com/mcp
```

- **使用 /mcp 命令进行身份验证**

```shell
> /mcp
```

在 Claude Code 中，使用 `/mcp` 命令管理身份验证，这会打开一个交互式菜单，您可以：

- 查看所有服务器的连接状态
- 与需要 OAuth 的服务器进行身份验证
- 清除现有身份验证
- 查看服务器功能
- **完成 OAuth 流程**
当您为服务器选择 " 身份验证 " 时：
1. 您的浏览器会自动打开到 OAuth 提供商
2. 在浏览器中完成身份验证
3. Claude Code 接收并安全存储访问令牌
4. 服务器连接变为活动状态

### 从 JSON 配置添加 MCP 服务器

假设您有一个单个 MCP 服务器的 JSON 配置，您想要将其添加到 Claude Code。

```shell
# 基本语法
claude mcp add-json <name> '<json>'

# 示例：使用 JSON 配置添加 stdio 服务器
claude mcp add-json weather-api '{"type":"stdio","command":"/path/to/weather-cli","args":["--api-key","abc123"],"env":{"CACHE_DIR":"/tmp"}}'

# 验证
claude mcp get weather-api
```

**注意：**
- 确保 JSON 在您的 shell 中正确转义
- JSON 必须符合 MCP 服务器配置模式
- 您可以使用 `-s global` 将服务器添加到您的全局配置而不是项目特定配置

### 从 Claude Desktop 导入 MCP 服务器

```shell
# 基本语法 
claude mcp add-from-claude-desktop
```

### 将 Claude Code 用作 MCP 服务器

假设您想要将 Claude Code 本身用作其他应用程序可以连接的 MCP 服务器，为它们提供 Claude 的工具和功能。

- 将 Claude 启动为 MCP 服务器

```shell
# 基本语法
claude mcp serve
```

- 从另一个应用程序连接
您可以从任何 MCP 客户端连接到 Claude Code MCP 服务器，例如 Claude Desktop。如果您使用 Claude Desktop，可以使用此配置添加 Claude Code MCP 服务器：

```json
{
  "command": "claude",
  "args": ["mcp", "serve"],
  "env": {}
}
```

**提示：**
- 服务器提供对 Claude 工具的访问，如 View、Edit、LS 等
- 在 Claude Desktop 中，尝试要求 Claude 读取目录中的文件、进行编辑等
- 请注意，此 MCP 服务器只是将 Claude Code 的工具暴露给您的 MCP 客户端，因此您自己的客户端负责为单个工具调用实现用户确认

### 将 MCP 提示用作斜杠命令

MCP 服务器可以公开在 Claude Code 中作为斜杠命令可用的提示。

- 发现可用提示
键入 `/` 以查看所有可用命令，包括来自 MCP 服务器的命令。MCP 提示以格式 `/mcp__servername__promptname` 出现。
- 执行不带参数的提示

```shell
> /mcp__github__list_prs
```

- 执行带参数的提示
许多提示接受参数。在命令后以空格分隔传递它们：

```shell
> /mcp__github__pr_review 456
> /mcp__jira__create_issue "Bug in login flow" high
```

**提示：**
- MCP 提示从连接的服务器动态发现
- 参数根据提示的定义参数进行解析
- 提示结果直接注入到对话中
- 服务器和提示名称已标准化（空格变为下划线）

## 添加 MCP

#### 必备的 MCP

- context7
- sequential-thinking
- figma
- Playwright? 有人反馈这个在 CC 上不好用，会读取无用的 html/css/js 等
- Zen MCP

```shell
# 添加context7
claude mcp add --transport http context7 https://mcp.context7.com/mcp

# 添加sequential-thinking
claude mcp add sequential-thinking npx @modelcontextprotocol/server-sequential-thinking

# 添加puppeteer
npx @modelcontextprotocol/server-puppeteer

claude mcp add puppeteer npx @modelcontextprotocol/server-puppeteer

# 添加magic (https://21st.dev/magic/onboarding?step=create-component)
claude mcp add magic npx @21st-dev/magic@latest --env API_KEY=你的api key

```

#### Puppeteer：浏览器自动化操作

<https://github.com/modelcontextprotocol/servers-archived/tree/main/src/puppeteer>

**一般添加方法如下：**

```shell
claude mcp add puppeteer npx -- -y @modelcontextprotocol/server-puppeteer
```

**通过 JSON 方式添加：**

```shell
claude mcp add-json -s user puppeteer '{  
  "command": "npx",  
  "args": ["-y", "@modelcontextprotocol/server-puppeteer"]  
}'
```

> 使用 `-s user` 标志，可以将 MCP 服务器添加到全局配置（可以在 `~/.claude.json` 文件中查看），而不是只针对某个项目，默认不填为 `local`  即当前项目。

**使用：**

> 打开搜索用户页面，按 ID 搜索 6 并返回搜索出来的用户信息

**查看添加**：

```shell
claude mcp add-json -s user context7 '{ "command": "npx", "args": ["-y", "@upstash/context7-mcp"] }'
```

#### context7

<https://context7.com/>

<https://github.com/upstash/context7>

它可以为大模型和 AI 代码编辑器提供最新（或者特定版本）的**文档、库、代码、信息**等，避免使用过时的数据，

在 Claude Code 中进行导入：

```shell
claude mcp add-json -s user context7 '{ "command": "npx", "args": ["-y", "@upstash/context7-mcp"] }'
```

#### Figma

见：[Mcp-Figma](Mcp-Figma.md)
