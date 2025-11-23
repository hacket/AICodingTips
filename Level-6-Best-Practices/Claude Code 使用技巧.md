---
banner: 
date_created: Sunday, July 20th 2025, 1:10:05 am
date_updated: Friday, October 31st 2025, 8:55:41 am
title: 03-Claude Code 使用技巧
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
aliases: [Claude Code 使用技巧]
linter-yaml-title-alias: Claude Code 使用技巧
---

# Claude Code 使用技巧

## Context 技巧

### CLAUDE.md

见 [CLAUDE.md文件](CLAUDE.md文件.md)

### 文件/文件夹/图片上下文

**1、拖入代码库中的文件夹或文件**

不限于当前的代码库，也包括其他代码库中的其他文件夹。比如可以把后端目录一起拖进来，让它理解整体架构，甚至直接改后端。用这种方法也可以增加处理多个代码库的功能。

**2、通过 URL 访问文档**

Claude Code 自带浏览器能力，可以粘贴文档链接，它会访问那个网站，阅读文档并获取它需要的任何上下文；或直接告诉它 " 用最新 Google Calendar API"，它会自行搜索并查阅文档获取 API 使用方式。

**3、拖动/复制图片处理到 Claude Code**

Claude Code 可以发送图片并进行处理，在命令行中，把图片和提示词发过去，让它更好的理解你的意图。

> 注意，在 Mac 中粘贴图片不是使用 command + v，而是使用 **control + v** 快捷键。
> Windows 似乎不能 ctrl+v，只能拖进来

也可以用 puppeteer mcp 来自动化应用的截图

### XML 标签结构化提示

Claude 对结构化语言比较敏感，使用类似 XML 的分块格式，可以显著提升提示词的清晰度与可控性。推荐使用如下结构：

```xml
<instruction>
你希望 Claude 执行的主要任务或目标
</instruction>

<context>
任务的背景信息，比如涉及的框架、业务逻辑、团队规范等
</context>

<code_example>
可以参考的代码片段、接口规范或已有实现
</code_example>
```

这种写法能帮助 Claude 更准确地区分 "**你要它做什么**" 和 "**你提供了哪些辅助信息**"，避免它把背景当成目标来执行。

### Prompt 指令

- **明确且具体的指令**：给出精确需求、边界条件与成功标准；显式引用文件；必要时附图片/URL。
- **任务拆细**：小步快跑、可回滚：小范围迭代与审阅
- 先理解项目代码再开动
- 输错指令，按 ESC，随时打断它工作；及时中断纠偏与撤销；避免一次性大变更。

### 追踪每一次 session

- 你在做什么？
- 你在会议中做了什么？
- 哪些有效？哪些无效？
- 下一步是什么？

我使用 Claude Sessions 命令来实现这一点，这样我就能记住我所构建的一切（并且可以用于未来的上下文）

<https://github.com/iannuttall/claude-sessions>

### 上下文占用查看

内置命令：/context

![PixPin_2025-10-11_00-07-39.png](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidian/202510110007766.png)

### 保持上下文专注（重要！）

保持上下文专注

- 任务间多用 `/clear` ，一个任务完成后开新的会话
- 在自然断点用 `/compact`

**其他：**
![PixPin_2025-10-11_00-11-30.png](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidian/202510110011875.png)
- 删除无用的 MCP，仅保留必要的
Mcp 也是相当占用 context 的，比如 `chrome-devtools-mcp` 、`zen mcp`

- 关掉 auto compat (`Autocompact buffer: 45.0k tokens (22.5%)`)
auto compat 占用了 45K，关闭 `/usage`，选择 config，关闭 auto compat

- 保持 CLAUDE.md 简洁
SuperClaude 引入了大量的 context，看上面 Memory files 占用了 21K，去掉 SuperClaude 后只有 4K 了

- 自定义的 sub agent 占用了 12K，可适当移除不需要的
- 上面所有的都做完，能拿到 180+K 的上下文
![PixPin_2025-10-11_00-29-39.png](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidian/202510110029638.png)

### 上下文懒加载

官方还未实现，有 issue 提了：

- <https://github.com/anthropics/claude-code/issues/8997>  
- <https://github.com/anthropics/claude-code/issues/7336>

比如 mcp、slash command、sub agents 等的懒加载，避免将 context 撑爆

或者用完一个 mcp 就移除，用的时候再添加

## 工具

### 修改工具的默认权限

工具的权限并不是一成不变的，可以通过 `--allowedTools` 或 `--disallowedTools` 参数修改工具的默认权限：

```shell
claude --allowedTools "Edit,MultiEdit,Write"
```

`--allowedTools` 是将工具的权限从用户确认改成自动放行，而 `--disallowedTools` 是将工具直接从工具列表中移除。**貌似不能将工具的权限从自动放行改成用户确认。**

这两个参数都可以在会话过程中通过 `/permissions` 或 `/allowed-tools` 斜杠命令进行查看和修改

### 额外的工作目录

默认情况下，Claude Code 只允许访问当前工作目录下的文件，在访问工作目录外的文件时，也会要求用户确认；

我们可以在启动时通过 `--add-dir` 参数添加额外的工作目录：

```shell
claude --add-dir ../browser-use
```

或者在会话中使用 `/add-dir` 斜杠命令：

```shell
/add-dir ../browser-use
```

这个参数也可以在会话过程中通过 `/permissions` 或 `/allowed-tools` 斜杠命令进行查看和修改；

所有允许访问的目录均显示在 `Workspace` 页签下，额外的工作目录遵循和原始工作目录相同的权限规则：读取文件无需确认，编辑文件则根据当前的权限模式决定是否确认。

### 工具更细粒度的权限控制

在调用某些工具时，我们可能还需要有更细粒度的权限控制，比如可以允许 `Bash` 执行特定命令，拒绝 `Read` 读取某些文件，等等，Claude Code 支持在工具名后面加上特定的匹配规则，比如下面这个例子：

```shell
claude --allowedTools "Bash(npm run build)"
```

当使用 `Bash` 工具运行 `npm run build` 命令时，直接放行，无需用户确认。也可以在匹配规则中使用通配符：

```shell
claude --disallowedTools "Bash(git:*)"
# 当使用 Bash 工具运行以 git 开头的命令时，直接拒绝
```

> Claude Code 能很好的处理 Shell 操作符（比如 `&&`），因此像 `Bash(safe-cmd:*)` 这样的前缀匹配规则不会给它运行命令 `safe-cmd && other-cmd` 的权限。

另外，`Read` 和 `Edit` 也有一套自己的匹配规则，比如：

```shell
claude --allowedTools "Edit(docs/**)"
```

上面的命令允许对项目 docs 目录中文件进行编辑，其中的 `docs/**` 规则遵循 gitignore 规范。还可以使用 `//` 引用绝对路径，或者 `~/` 引用用户目录的路径：

- `Edit(//tmp/scratch.txt)` 匹配对 `/tmp/scratch.txt` 的编辑
- `Read(~/.zshrc)` 匹配对用户的 `~/.zshrc` 文件的读取

值得注意的是，`Read` 的规则将应用于所有读取文件的内置工具，如 `Grep`、`Glob` 和 `LS`。除了命令执行和文件操作，下面这些工具也支持细粒度控制：

- `WebFetch(domain:example.com)` 匹配对 `example.com` 的抓取请求
- `mcp__amap` 匹配由 MCP 服务器 `amap` 提供的任何工具
- `mcp__amap__weather` 匹配由 MCP 服务器 `amap` 提供的 `weather` 工具

### 权限模式

Claude Code 支持几种不同的权限模式：

- **默认模式（`default`）**：按照默认或用户配置的权限规则对工具进行验证
- **自动编辑模式（`acceptEdits`）**：自动接受对工作目录下的文件的编辑
- **规划模式（`plan`）**：只能读取文件进行分析，不允许编辑文件或执行命令
- **YOLO 模式（`bypassPermissions`）**：跳过所有权限验证，危险！

### 配置文件

除了命令行参数和斜杠命令，Claude Code 还支持将工具的权限保存在配置文件中；

当同一个工具的规则出现在多个位置时，优先级从高到低如下：**企业管理策略 > 命令行参数 > 本地项目设置 > 共享项目设置 > 用户设置**。这样的层次结构确保始终执行企业策略，同时在适当的情况下仍允许在项目和用户级别的灵活性。

- 用户设置（`~/.claude/settings.json`）：用户私有，适用于所有项目
- 共享项目设置（`.claude/settings.json`）：提交到 Git 仓库，团队成员共用
- 本地项目设置（`.claude/settings.local.json`）：不提交到 Git 仓库，用户私有，只适用于当前项目
- 企业管理策略（`/path/to/policies.json`）：在企业环境下，系统管理员可以强制执行用户无法覆盖的安全策略，优先级最高

**配置文件模板：**

```json
{  
  "env": {  
    "ANTHROPIC_AUTH_TOKEN": "sk-0rsmP4CR591NN5eMEA5nxvT0g4M52TvUm91r9qLU4QdfwR8O",  
    "ANTHROPIC_BASE_URL": "https://anyrouter.top"  
  },  
  "permissions": {  
    "allow": [  
      "WebFetch(domain:rube.app)",  
      "Bash(dir:*)",  
      "Bash(ping:*)",  
      "Bash(wmic:*)",  
      "Bash(powershell:*)",  
      "Bash(net stop:*)",  
      "Bash(net start:*)",  
      "Bash(npm run lint)",  
      "Bash(npm run test:*)",  
      "Read(~/.zshrc)",  
      "Search(*)",  
      "Search(pattern:*)",  
      "Search(pattern:*, include:*)",  
      "Read(*)",  
      "Edit(*)",  
      "Write(*)",  
      "Bash(git:*)",  
      "Bash(git:add)",  
      "Bash(git:add,commit)"  
    ],  
    "deny": [  
      "Bash(curl:*)"  
    ],  
    "ask": [],  
    "defaultMode": "bypassPermissions",  
    "additionalDirectories": [  
      "D:\\android\\AndroidStudioProjects\\OpenSources"  
    ]  
  },  
  "hooks": {},  
  "statusLine": {  
    "type": "command",  
    "command": "bun x ccusage statusline"  
  }  
}
```

## Claude Code 模式

#### 用好无头模式 -p

**什么是无头模式？**
Claude Code 的无头模式（headless mode） 专为非交互式环境设计，如 CI/CD、Git 钩子、自动化脚本等。

- 使用 `-p` 标志并附带一个提示词即可启用。
- 使用 `--output-format stream-json` 用于流式 JSON 输出。

> 请注意，无头模式在会话之间不会持续存在。您必须在每个会话中触发它。

**无头模式应用**

- 无头/CI 自动化：在脚本与 CI 中使用无头模式执行检查、分流或结构化流程。
- 自动化工作流。
`claude -p`（无头模式）以编程方式将 Claude Code 集成到更大的工作流程中，同时利用其内置工具和系统提示符。使用无头模式主要有两种模式：

- **Fanning out** 扇出 处理大型迁移或分析（例如，分析数百个日志中的情绪或分析数千个 CSV）：
	- 让 Claude 编写一个脚本来生成任务列表。例如，生成一个包含 2k 个文件的列表，这些文件需要从框架 A 迁移到框架 B。
	- 循环执行每个任务，以编程方式调用 Claude，并赋予其一个任务和一组可用的工具。例如：`claude -p “migrate foo.py from React to Vue. When you are done, you MUST return the string OK if you succeeded, or FAIL if the task failed.” --allowedTools Edit Bash(git commit:*)`
	- 运行脚本几次并优化提示以获得所需的结果。
- **Pipelining** 管道 将 Claude 集成到现有的数据处理管道中。
	- 调用 `claude -p “<your prompt>” --json | your_command`，其中 `your_command` 是处理管道的下一步
	- 就是这样！JSON 输出（可选）可以帮助提供更易于自动化处理的结构。

对于这两种用例，使用 `--verbose` 标志来调试 Claude 调用都会很有帮助。为了获得更清晰的输出，我们通常建议在生产环境中关闭详细模式。

#### 免授权模式 (Bypassing Permissions)

你是不是经常遇到 Claude Code 干活干一半，停下来让你授权？

不授权就卡在那里，虽然可以在当前会话可以设置不再询问，但权限又有好几种，每种权限都要来问一下，严重影响效率。

其实，启动 claude 时有一个参数：

```shell
claude --dangerously-skip-permissions

# 封装成shell 函数
function cc() {
  # yolo 开启claude code无需权限模式
  if [[ "$1" == "yolo" ]]; then
    command claude --dangerously-skip-permissions
  else 
    command claude "$@"
  fi
}
```

带上这个参数启动时，Claude Code 会出现警告提示：

![image.png](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidian/20250808003204277.png)

你需要点确认（Yes）才能开启 **Bypassing Permissions** 模式，开启此模式后，终端下面会出现黄色的 `Bypassing Permissions` 模式提示：

![image.png](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidian/20250808003204288.png)

开启 **Bypassing Permissions** 模式后，后面所有操作就都不需要你授权了，Claude Code 哐当就把所有活干了。

每次都输入 `claude --dangerously-skip-permissions` 太麻烦了，还可能输错，可以考虑他那一个 alias 别名：

```shell
alias claude='claude --dangerously-skip-permissions'
```

这只是临时生效，永久生效可以把它放到个人环境配置文件中，然后 source 生效一下。

把这个加入 `~/.claude/settings.json` 就不用每次手动输入 `claude --dangerously-skip-permissions` 了

```json
{
	"permissions": {
		"defaultMode": "bypassPermissions"
	}
}
```

## subagents

多用 subagents

## hooks

##### 免授权模式【坑】

要开启免授权模式，一般是需要配合 git 版本控制的；防止修改了没有 git 版本的文件，  

> 如：让 CC 检查下整个项目是否有密钥泄漏可能，CC 认为 `.env` 里的密钥可能泄漏，就给改了，.env 配置在 gitignore 文件不会提交到 git，这样就找不回原来的密钥了

**免授权模式注意：**
对没有纳入版本控制的文件的修改，最好是通过 hooks 拦截下，修改前做好备份或二次的确认

#### Plan 模式: Claude 真正发挥实力的关键 (plan mode)

Plan 模式是 Claude Code 最强大的特性之一，却经常被忽略或误用。  
只需按下 `Shift + Tab` 两次，即可进入 Plan 模式。在这里，你应该用自然语言清晰描述自己希望 Claude 执行的任务。Claude 会先帮你生成一个详细的执行计划，而不是直接生成代码。  
两个核心建议：

- 每一步都用 Plan 模式：别偷懒，每个微任务都应该规划。
- 搭配模型更高效：规划用 Opus，执行用 Sonnet，质量更高还省钱。

![image.png](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidian/20250808003204290.png)

> 在项目前期需要规划功能的时候可以用到这个模式，它会自动给到计划方案，然后底部你是否执行：如点击第一个选项 `Yes, and auto-accept edits`，它就会进入「**自动接受编辑**」模式，根据 todo list 完成所有之前规划的功能。

按下 `shift + tab` 键，可以在**一般模式、auto-accept edits、plan mode**之间来回切换。

#### 自动接受编辑 ( auto-accept edits)

在 Claude Code 中，可以通过按下 `shift + tab` 键来切换到「**自动接受编辑**」功能（**auto-accept edits on**）:

![image.png](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidian/20250808003204291.png)

开启此功能后，Claude Code 会自动创建、编辑文件，**而不是每次都需要我们手动确认**。

> 和 `--dangerously-skip-permissions` 模式相比，自动接受编辑功功能安全性要更高，首先它不是全局的，自动审批权限范围也仅限文件编辑。

## 安全

### 权限

**权限与安全**：配置允许列表；谨慎使用自动批准；仅在受限环境且有备份时考虑 YOLO（`--dangerously-skip-permissions`）

#### 必备的一些权限

### 禁止区域

**划定 " 禁止触碰 " 区域**：迁移脚本、API 契约、机密配置与安全关键代码由人掌控，并加边界提示。

#### 安全审查：AI 代码最大风险来自 " 安全盲区 "

大多数新手开发者会忽视安全问题，而 Claude 默认并不会主动防御所有安全漏洞。  
解决方法：每写完一段功能后，发送如下 Security prompt:

```
Please check through all the code you just wrote and make sure it follows security best practices. make sure there are no sensitive information in the front and and there are no vulnerabilities that can be exploited.
```

这是防止 `API 密钥暴露`、`XSS 漏洞` 等问题的有效手段，尤其适合准备上线的产品。  
也可以在任务结束后，要求它检查是否破坏其他功能、尝试找找边缘情况，确认是否一切正常。它总能找到我们忽略的东西，这可以让我们对它生成的代码多一点心安。

定义一个 slash command 或 subagent 实现安全审查

## 工作流

### Claude Code 的高效工作流

先用 Plan Mode 规划，再用 TDD 执行。

**具体操作流程** ⬇️  
1. 进入 Plan Mode，与 Claude 充分讨论设计架构、功能细节和边界条件，确认思路与测试方法。  
2. 明确计划后，退出 Plan Mode，开始执行。  
3. 使用 TDD 小步迭代：  
	- 先写测试，让测试失败（Red）；  
	- 再逐步实现功能，通过测试（Green）；  
	- 最后对代码重构优化（Refactor）。

**辅助技巧**
➡️ 在 prompt 里加入关键词 think through，激发 Claude 深度思考能力；  
➡️ 使用 /compact 定期清理上下文，提高 AI 稳定性；  
➡️ 在项目根目录创建 CLAUDE.md，定义项目规范和规则，减少误解需求的风险。

### 测试驱动开发

测试优先且由人书写：倾向 TDD；每次小改动后立刻运行测试/类型检查/格式校验；避免让 AI 修改关键测试或断言。

### Git & Github

#### 用 GitHub 模拟 " 撤回 " 功能：Claude 没有回溯按钮怎么办

Claude Code 不像 Cursor 那样有 " 撤回到某步 " 的 `Checkpoint` 功能，因此你需要手动保存版本。

建议做法：每当 Claude 成功执行一个任务，立即 commit 到 GitHub；出错时，回退到上一个版本重新开始。这样能让你拥有几乎等效的 " 时间穿梭机 "。

#### 使用 Git worktrees

在使用 Claude Code 时，如果你希望同时处理多个任务、多个分支，并让每个实例彼此完全隔离，Git worktrees 是非常实用的方案。

Git worktree 允许你将同一个 Git 仓库的不同分支分别检出到独立的目录中。每个 worktree 有自己的工作目录、隔离的文件状态，但共享相同的 Git 历史。

**1、创建新的 worktree**

```shell
# 如果你要创建新的分支并启动一个新的工作副本：
git worktree add ../project-feature-a -b feature-a

# 如果你已经有一个现成的分支：
git worktree add ../project-bugfix bugfix-123
```

这会在项目外部（如 `../project-feature-a`）创建一个独立的目录，其中包含该分支的完整工作目录。

**2、在每个 worktree 中运行 Claude Code**

```shell
# 进入新的 worktree：
cd ../project-feature-a
claude

# 再开一个 worktree：
cd ../project-bugfix
claude
```

每个会话运行在各自独立的代码环境中，Claude Code 实例互不干扰。

**3、管理 worktree**

```shell
# 列出当前所有 worktree：
git worktree list

# 删除一个 worktree：
git worktree remove ../project-feature-a
## 注意：删除 worktree 不会删除 Git 分支，只会清理目录。

```

**注意：**
- 每个 worktree 相当于独立的 Claude Code 沙盒，适合并行处理多个任务（如 bug 修复、特性开发、重构）。
- 在一个 worktree 中的更改不会影响另一个 worktree。
- 所有 worktrees 共享相同的 Git 历史和远程设置，便于统一推送。
- 使用有意义的目录名（如 `project-auth`, `project-api-v2`）能帮助你快速区分任务。
- 每个新 worktree 创建后，务必初始化开发环境，例如：
	- **JavaScript 项目**：`npm install`  
	- **Python 项目**：python -m venv .venv  
		source .venv/bin/activate  
		pip install -r requirements.txt

## 实用

### 扮演 Linus Torvalds

### Telegram 源码

想要什么牛逼效果，就让 ClaudeCode 调查 Telegram 的源码。这个源码库就是大学、就是殿堂、就是一群把 UIKit 玩儿出花儿的人写出来的。高性能照片选择器，极致的 Cell 复用的滚动条。他们为了让键盘弹出的时候页面配合良好，竟然他妈的逆向得到了系统键盘弹出的动画曲线参数，然后 1:1 对齐

![image.png](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidian202509160900338.png)

## 其他

#### 3 条铁律让你告别代码屎山

<https://mp.weixin.qq.com/s/jQRB9B9Nt0-_5QPgq4_6TA>

##### 1、沟通需求时，用飞书文档

和 Claude Code 沟通新需求时，用飞书文档写需求，做到「任何人看都没有歧义」。需求描述超过 1000 字，图文并茂，然后复制给 Claude Code

> 尝试让 Claude Code 直接写代码，是新手最容易犯的第一个错误。特别容易把代码改成屎山。

一定要意识到：如果代码成了屎山，这不是 Claude Code 的问题，是你的问题。  

新手并容易不知道自己是否把需求描述得没有歧义，他们会倾向于甩锅给 AI。为了万无一失，你还需要看下一条。

##### 2、先理解需求，不要急着写代码

新需求首次沟通时，末尾强调 「不要急着写代码！先理解需求，给出实现思路，我们先讨论，看还有啥需要我决策的点？ultrathink 」

> 尝试让 Claude Code 直接写代码，是新手最容易犯的第二个错误

有同学问题我，为什么不用 Plan Mode？ 是的，Plan Mode 可以得到类似的效果，但是，切换模式有点麻烦了。我喜欢提前授予 Claude Code 一切权限，解放双手。

一般而言，新需求，需要反复讨论 3～5 轮，直到 Claude Code 完全找不出来下一个需要你决策的点，我们再让它开始写代码。

##### 3、界面需求用 ASCII 码画出来

涉及界面需求时：快速纸上画布局，然后让 Claude Code 用 ASCII 画出来，最后提醒它拆分控件

A.关于画草图，最快的是在纸上画，也可以在 Excalidraw 上画，怎么快怎么来。无论怎么画，Claude Code 都能明白你的意思。

B.关于 ASCII 画图，你可以让 Claude Code 出 3~5 种不同的布局，然后你来选择。

C. 最后，在开始编码前，强调让 Claude Code 仔细理解项目结构，尽可能合理地拆分控件、并把控件放到合适的位置。 这也是新手常见坑，如果不做强调，Claude Code 可能会写出来单文件很大的控件。

#### 善用截图：灵感输入和 UI 调试的利器

Claude 支持图片输入功能，这让它在 UI 开发中如虎添翼。

- **场景一：界面灵感输入**  
用截图工具（如 Mac 上的 `Command + Shift + 4`）截取目标 UI，然后上传至 Claude，配合提示语 " 请参考这个截图构建界面 "，Claude 会精准复刻。

- **场景二：调试 Bug 或优化 UI**
截图错误页面或丑陋界面，交给 Claude，它能帮你自动修复。

#### 用好 /clear：节省成本、降低幻觉的法宝

长时间与 Claude 交互，会积累大量上下文信息，导致回复变慢、误差增多，甚至消耗大量 token。

建议：每完成一个阶段性任务，立即使用 `/clear` 命令，清除上下文。这不仅能让 Claude 表现更精准，还能显著节省月度额度。

#### 向 Claude 学习：提升 Prompt 水平的秘密武器

Claude 不只是工具，也是你的 AI 教练。  
每完成一个功能，不妨这样问 Claude：

```
Please explain the functionality and code you just built out in detail. Walk me through what you changed and how it works. Act like you’re a senior engineer teaching me code.
```

这样做能显著提升你对代码逻辑的理解，从而更精准地下达指令，最终获得更高质量的输出。

#### 运行子代理：效率倍增

Cloud Code 有能力启动子代理，在做非常庞大的任务时，可以让它拆分问题并同时跑多个 `sub-agent`。每个 sub-agent 拥有它们自己的上下文，会并行地执行任务，速度快非常多。

#### 等待 Claude 运行时保持专注的秘诀：用 Claude 当 " 陪伴教练 "

Claude 生成代码有时需要数分钟。在此期间，你是否会刷视频、走神、浪费时间？  
一个巧妙的方式可以帮你改变这个习惯：  
每当 Claude 正在执行任务，你就打开另一个 Claude 会话，与之探讨产品创意、复盘任务目标、制定下一步计划，进行头脑风暴。  
不仅避免了 " 精神内耗 "，还极大提升了效率和心态。

#### 激活 " 思考模式 "，攻克复杂问题

Claude Code 内置了一种特殊的深度推理模式，只需在指令中加入特定关键词，就能自动触发。

在 Claude Code 中，可以使用 "**think**" 这个词来激活深度思考模式，包括以下几种级别：

```shell
“think” < “think hard” < “think harder” < “ultrathink”
```

使用这些深度思考，会直接对应系统中不同级别的思考预算，每一级都会逐步增加 Claude 可用的思考预算，毫无疑问，使用 `ultrathink` 是最费钱的，也能发挥它的最大潜能。

如果你是订阅的是 Max 套餐，可以考虑使用 `ultrathink` 模式，不然就得小心你的钱包。

**示例：**

```shell
1+1=？ultrahink

# 一个 1+1 计算耗费了 0.06 美元，大概不到 5 毛 RMB。。
```

### 善用快捷键

- 输入 `/` 查看所有斜杠命令；
- 使用 `上下方向键` 查看命令历史；
- 使用 Tab 键进行命令快速补全；
- 使用 `Option + Enter` 换行；
- 使用 `Ctrl + C` 退出终端等等。
