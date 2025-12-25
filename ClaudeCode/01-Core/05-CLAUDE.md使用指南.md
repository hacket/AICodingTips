
# CLAUDE.md 文件

## CLAUDE.md 文件基础

### CLAUDE.md 是什么？

`CLAUDE.md` 文档是为 Claude Code 提供项目特定上下文和指令的配置文件。这些文件充当项目的持久记忆（Memory），Claude Code 在运行时会自动读取并添加到上下文中作为系统提示词（System Prompt）。

### CLAUDE.md 分级

CLAUDE.md 分为四个层级：

![image.png](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidian/202510282355487.png)

作为个人用户，我们只需要关注用户级别和项目级别的 CLAUDE.md 文档配置即可。

- 其中用户级别的配置可以视作你的 Claude Code 编码全局配置，配置地址为 `~/.claude/CLAUDE.md`，用于跨所有项目的全局指令。
- 项目配置的 CLAUDE.md 可以直接放置在项目根目录下或者一些子目录下：`./CLAUDE.md` 或 `.claude/CLAUDE.md`。

CLAUDE.md 文档一般可以包含编码指南和标准、项目特定上下文、常用命令或工作流程、API 约定以及测试要求等信息。

### /init 初始化 claude.md

**初始化**
每次新的项目，调用 `/init` 命令，生成 CLAUDE. md

验证效果：初始化后，试着问 Claude Code 几个问题，确认它是否理解项目：

· 这个项目是做什么的？

· 文件夹结构是怎样的？

· 项目用了哪些技术？

如果回答得不够好，可以让 Claude Code 根据初步理解优化 CLAUDE.md 文件。

**信任 /init 命令**
- 永远相信 `/init`
- 定期使用 `/init` 命令让您的 `CLAUDE.md` 保持最佳状态
- 对于重要功能，在子文件夹中创建 `CLAUDE.md` 文件，以在每个级别维护上下文和最佳实践

**为什么有效：**
- 保持项目上下文的新鲜和相关
- 确保 Claude Code 拥有关于代码库的最新信息
- 在不同项目领域保持一致性

### 调优 claude.md

#### **1、基本调优：**

- 调优 `CLAUDE.md`，以达到最佳状态
- 定期优化和精简 claude. md 文件，保持其具体和高效性
- 在仓库根目录（以及子目录/用户目录）维护精炼的 CLAUDE. md；
- 用 `#` 快速沉淀命令、规范与重要规则。

#### **2、使用 Anthropic 提示词优化工具优化 claude. md**

- [Use our prompt improver to optimize your prompts - Anthropic](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/prompt-improver)
![](https://mintlify.s3.us-west-1.amazonaws.com/anthropic/images/prompt_improver_modal.png)

#### **3、配合 Deep Graph MCP**

让 Claude Code 读取项目的 README. md，结合 Deep Graph MCP 的强大功能，再次更新 CLAUDE. md。用 Deep Graph MCP，让 Claude Code 能更深入地分析代码库，比如进行语义搜索、节点搜索，全面提升上下文理解能力。

```markdown
1. 注册 CodeGPT 账号，在 “API Connections” 页面获取：
   · API 密钥（`YOUR_CODEGPT_API_KEY`）
   · 组织 ID（`CODEGPT_ORG_ID`）
2. 将你的代码库上传到 CodeGPT 的 Code Graph，获取 CODEGPT_GRAPH_ID。
3. 运行以下命令安装 Deep Graph MCP：
   claude mcp add "Deep Graph MCP" npx -- -y mcp-code-graph@latest YOUR_CODEGPT_API_KEY CODEGPT_ORG_ID CODEGPT_GRAPH_ID
4. 验证安装是否成功：
   claude mcp list
   claude mcp get "Deep Graph MCP"
注意：如果你的代码库是私有的，参考 CodeGPT 的完整教程。
```

为什么：这能确保 Claude Code 对项目的理解达到最佳状态，即使你提出模糊或复杂的问题，它也能准确应对。

#### 不要用一个巨大的文件，使用文档引用

```markdown
### 🗺️ 关键文档引用
- **Docker 架构**: `/docs/DOCKER_ARCHITECTURE.md` 🐳
- **数据库架构**: `/docs/DATABASE_ARCHITECTURE.md`
- **密码真相**: `/docs/PASSWORD_TRUTH.md` 🚨 先读这个！
- **JWT 认证**: `/docs/JWT_AUTHENTICATION_ARCHITECTURE.md` 🔐
- **安全检查清单**: `/docs/SECURITY_CHECKLIST.md` 🚨
- **功能请求**: `/docs/enhancements/README.md`
- **健康监测 V2**: `/docs/enhancements/HEALTH_MONITORING_V2.md` 🆕
```

### 用好 claude.md: 写出 " 零 Bug" 代码的关键

Claude Code 支持自定义规则文件 `claude.md`，这是许多用户忽视的神技，它是 Claude 的 " 工作手册 "，包含项目规则与流程规范。

你可以在项目目录中添加这个文件，写入一套 "`任务驱动规则`"，引导 Claude 以 "`先规划、再执行`" 的方式逐步生成代码。这套七条规则能让 Claude 把每一个请求都拆解成清晰可控的任务，还能自动生成任务目录，确保每一步有迹可循。

```markdown
## First Plan
1. First think through the problem, read the codebase for relevant files, and write a plan to tasks/todo.md.  
2. The plan should have a list of todo items that you can check off as you complete them  
3. Before you begin working, check in with me and I will verify the plan.  
4. Then, begin working on the todo items, marking them as complete as you go.  
5. Please every step of the way just give me a high level explanation of what changes you made  
6. Make every task and code change you do as simple as possible. We want to avoid making any massive or complex changes. Every change should impact as little code as possible. Everything is about simplicity.  
7. Finally, add a review section to the todo.md file with a summary of the changes you made and any other relevant information.
```

立即复制这套规则并放入你的 `claude.md` 文件中，你会立刻感受到代码质量的巨大提升。

### 多级目录设置 claude.md

**将 CLAUDE.⁠ md 文件添加到子目录：**
这是让 Claude Code 不那么 "dumb" 的无名英雄。每个目录都可以有自己的规则文件，而不是一个庞大的规则文件：

```shell
/src/components/CLAUDE.md
/src/db/CLAUDE.md
```

这为 Claude 提供了更精确的背景，并带来了巨大的变化

也可以在用户目录设置一份全局的 claude. md，可以供所有项目使用

**注意：**
目前 Claude Code 不支持自动加载子目录的 CLAUDE. md 文件。这是 Claude Code 的设计限制。

**Claude Code 加载 Claude. md 规则：**
- 只加载当前目录：仅加载当前工作目录的 CLAUDE. md
- 不递归搜索：不会自动搜索和加载子目录的配置
- 设计原因：避免配置冲突和保持 context 的清晰性

## 开源的 CLAUDE. md

### Chris Dzombak

<https://github.com/LichAmnesia/GPT-Prompt-Hub/blob/main/CLAUDE.md>

这个全局 CLAUDE.md 配置参考的是国外顶级开发者 Chris Dzombak 写的 Claude Code 深度使用经验总结，其中核心的开发哲学是：

- 渐进式改进而非一次性大改动：进行小规模修改并确保通过测试
- 从现有代码中学习：在实施前进行研究和规划
- 务实而非教条：适应项目实际情况

跟 MCP 配置数量一样，CLAUDE.md 文档也并不是需要面面俱到，越长越好。太长的系统提示词会占据较多的上下文空间，一定程度上也会稀释真正的项目信息。

## 好用的 rules

### 任何项目都务必遵守的规则

```markdown
# 任何项目都务必遵守的规则（极其重要！！！）

## First Plan

1. First think through the problem, read the codebase for relevant files, and write a plan to tasks/todo.md.  
2. The plan should have a list of todo items that you can check off as you complete them  
3. Before you begin working, check in with me and I will verify the plan.  
4. Then, begin working on the todo items, marking them as complete as you go.  
5. Please every step of the way just give me a high level explanation of what changes you made  
6. Make every task and code change you do as simple as possible. We want to avoid making any massive or complex changes. Every change should impact as little code as possible. Everything is about simplicity.  
7. Finally, add a review section to the todo.md file with a summary of the changes you made and any other relevant information.

## Code Architecture

- 编写代码的硬性指标，包括以下原则：
  （1）对于 Python、JavaScript、TypeScript 等动态语言，尽可能确保每个代码文件不要超过 300 行
  （2）对于 Java、Go、Rust 等静态语言，尽可能确保每个代码文件不要超过 400 行；Android项目用Kotlin语言
  （3）每层文件夹中的文件，尽可能不超过 8 个。如有超过，需要规划为多层子文件夹
- 除了硬性指标以外，还需要时刻关注优雅的架构设计，避免出现以下可能侵蚀我们代码质量的「坏味道」：
  （1）僵化 (Rigidity): 系统难以变更，任何微小的改动都会引发一连串的连锁修改。
  （2）冗余 (Redundancy): 同样的代码逻辑在多处重复出现，导致维护困难且容易产生不一致。
  （3）循环依赖 (Circular Dependency): 两个或多个模块互相纠缠，形成无法解耦的“死结”，导致难以测试与复用。
  （4）脆弱性 (Fragility): 对代码一处的修改，导致了系统中其他看似无关部分功能的意外损坏。
  （5）晦涩性 (Obscurity): 代码意图不明，结构混乱，导致阅读者难以理解其功能和设计。
  （6）数据泥团 (Data Clump): 多个数据项总是一起出现在不同方法的参数中，暗示着它们应该被组合成一个独立的对象。
  （7）不必要的复杂性 (Needless Complexity): 用“杀牛刀”去解决“杀鸡”的问题，过度设计使系统变得臃肿且难以理解。
- 【非常重要！！】无论是你自己编写代码，还是阅读或审核他人代码时，都要严格遵守上述硬性指标，以及时刻关注优雅的架构设计。
- 【非常重要！！】无论何时，一旦你识别出那些可能侵蚀我们代码质量的「坏味道」，都应当立即询问用户是否需要优化，并给出合理的优化建议。

## Communication

- 永远使用简体中文进行思考和对话
- 行业的专业术语使用英文来对话，特别是计算机科学相关
  - 特别是Android开发领域的，如系统的类名，关键字
  - Gradle开发相关
  - Kotlin开发相关
  - Java开发相关
  - Python开发相关
  - HTML/CSS/JavaScript(JS)相关
  - AI相关

## Documentation

- 编写 .md 文档时，也要用中文，专业术语保留用英文
- 正式文档写到项目的 docs/ 目录下，文档名用英文
- 用于讨论和评审的计划、方案等文档，写到项目的 discuss/ 目录下
```

### 认知与工作的三层架构

低水平的编码人员，无法意识到代码中高层次的问题，从而只能指挥 AI 去修复表面的 bug，而无法从更高的架构层面来真正实现 " 干中学 "。那么这段提示词正是为了尝试解决这个问题。让 LLM 在 " 现象层 " 接收你的问题，但是在 " 代码哲学层 " 进行真正的思考，最终，在 " 架构本质层 " 进行排查和分析。好问题才有好答案？但是小白怎么可能提出好问题？所以死循环了。那么可以用这段提示词试一试。

- [认知与工作的三层架构- Linus Torvalds](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/prompts/%E8%AE%A4%E7%9F%A5%E4%B8%8E%E5%B7%A5%E4%BD%9C%E7%9A%84%E4%B8%89%E5%B1%82%E6%9E%B6%E6%9E%84-%20Linus%20Torvalds.md)

### 扮演 Linus Torvalds

模拟 Linus Torvalds 的 prompt，还挺能喷的

- [Linus Torvalds](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/prompts/Linus%20Torvalds.md)

### RMS（Richard Stallman）風格靈感

见 [[RMS灵感]]
