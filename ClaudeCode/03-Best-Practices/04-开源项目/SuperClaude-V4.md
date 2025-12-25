
# SuperClaude V4

<https://github.com/SuperClaude-Org/SuperClaude_Framework>

## V4 相比 V3 的改进

- **21 specialized commands**：命令从 V3 版本的 17 个 增加到 21 个
- **13 specialized agents**：V3 版本的 persona system 转换为了 subagent
- **4 Behavioral Modes**：不同的工作用不同的 mode (Brainstorming, Introspection, Task Management, Token Efficiency)
- **6 MCP servers**：MCP 集成
- **Session Lifecycle**：会话持久化管理，通过命令：`/sc:load` and `/sc:save`
- **增强的 Hook 系统**：可扩展和可自定义
- **SuperClaude-Lite**： 轻量级版本

## 安装

### 卸载 V3

从 V3 升级，需要先干净卸载 V3 版本

```shell
# Uninstall V3 first
Remove all related files and directories :
*.md *.json and commands/
./claude/commands/sc
./claude/superclaude-metadata.json # 有这个文件会导致如commands不会安装，升级的话最好移除该文件

# Then install V4
pipx install SuperClaude && pipx upgrade SuperClaude && SuperClaude install
```

### V4 安装

```shell
pip install SuperClaude
SuperClaude install
```

然后需要选择：

![obsidian202509250010763](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidianobsidian202509250010763.png)

### V4 安装了什么？

![obsidian202509250834653](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidianobsidian202509250834653.png)

- `~/.claude/`
	- `~/.claude/commands/sc` 目录下有 24 个 command
	- `~/.claude/commands/agents` 目录下有 15 个 agents，可以新建一个子目录 sc，都移动到这去
![obsidian202509250853650](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidianobsidian202509250853650.png)

- `~/.claude/CLAUDE.md`
会在 CLAUDE.md 后面追加下列内容：
也可以在 `~/.claude/` 新建 sc 目录，将这些移动进去，方便管理，需要更新下 `CLAUDE.md` 的文件引用

```markdown
# ===================================================
# SuperClaude Framework Components
# ===================================================

# Core Framework
@BUSINESS_PANEL_EXAMPLES.md
@BUSINESS_SYMBOLS.md
@FLAGS.md
@PRINCIPLES.md
@RULES.md

# Behavioral Modes
@MODE_Brainstorming.md
@MODE_Business_Panel.md
@MODE_Introspection.md
@MODE_Orchestration.md
@MODE_Task_Management.md
@MODE_Token_Efficiency.md

# MCP Documentation
@MCP_Context7.md
@MCP_Magic.md
@MCP_Morphllm.md
@MCP_Playwright.md
@MCP_Sequential.md
@MCP_Serena.md
```

- `~/.claude/*.md`
![obsidian202509250837949](https://raw.githubusercontent.com/hacket/ObsidianOSS/master/obsidianobsidian202509250837949.png)
- `~/.claude/.superclaude-metadata.json`

## 特性

### 22 Specialized Commands

**按功能分类：**
- **Planning**: brainstorm, design, workflow, estimate
- **Development**: implement, build, git
- **Analysis**: analyze, business-panel, troubleshoot, explain
- **Quality**: improve, cleanup, test, document
- **Management**: task, spawn, load, save, reflect
- **Utility**: index, select-tool

**按复杂度：**
- **Beginner**: brainstorm, implement, analyze, test
- **Intermediate**: workflow, design, business-panel, improve, document
- **Advanced**: spawn, task, select-tool, reflect

#### workflow

**作用：**
`/sc:workflow`，根据需求生成结构化实施计划

**语法：**` /sc:workflow "feature description" [--strategy agile|waterfall] [--format markdown]`

**案例：**

```shell
# Feature planning: 
/sc:workflow "user authentication"

# Sprint planning: 
/sc:workflow --strategy agile

# Architecture planning: 
/sc:workflow "microservices migration"
```

### 15 Specialized Agents

- 🏗️ **architect** - System design and architecture
- 🎨 **frontend** - UI/UX and modern frontend development
- ⚙️ **backend** - APIs, infrastructure, and server-side logic
- 🔍 **analyzer** - Debugging and system analysis
- 🛡️ **security** - Security assessment and vulnerability analysis
- ✍️ **scribe** - Technical documentation and writing
- ⚡ **performance** - Optimization and performance engineering
- 🧪 **qa** - Quality assurance and testing strategies
- 📊 **data** - Data analysis and processing
- 🤖 **devops** - Infrastructure and deployment automation
- 🔧 **sre** - Site reliability and system operations
- 💼 **product** - Product strategy and requirements
- 🎯 **specialist** - Adaptive expertise for unique domains

#### 2 种方式用 agents

##### 手动

输入 `@agent-` 前缀

```shell
@agent-frontend-architect "design responsive navigation"
```

##### 自动激活（Behavioral Routing）

自动更新上下文描述激活 agent

```shell
/sc:implement "JWT authentication"  # → security-engineer auto-activates
/sc:design "React dashboard"        # → frontend-architect auto-activates
/sc:troubleshoot "memory leak"      # → performance-engineer auto-activates
```

#### agent 选择规则

##### 优先级

- 手动覆盖
`@agent name` 优先级高于自动激活

- Keywords
直接领域术语触发主要 agent

- File types
扩展名激活语言/框架专家

- Complexity
多步骤任务需要协调 agent

- Context
相关概念触发互补 agent

##### 冲突解决

- Manual invocation → Specified agent takes priority
- Multiple matches → Multi-agent coordination
- Unclear context → Requirements analyst activation
- High complexity → System architect oversight
- Quality concerns → Automatic QA agent inclusion

#### The SuperClaude Agent Team

看一些能用得上的

### 6 Behavioral Modes

### 6 MCP Server Integration

- **Context7** - Official library documentation and patterns
- **Sequential** - Multi-step analysis and complex reasoning
- **Magic** - Modern UI component generation
- **Playwright** - Browser automation and E2E testing
- **Morphllm** - Intelligent file editing with Fast Apply capability
- **Serena** - Semantic code analysis and project-wide operations

### Session Lifecycle System

- **`/sc:load`** - 使用完整 context 恢复来初始化项目
- **`/sc:save`** - 创建检查点并保存会话状态
- **Automatic Checkpoints**
- **Cross-Session Learning**

### Hooks System

- **Framework Coordinator** - Cross-component orchestration
- **Performance Monitor** - Real-time metrics and optimization
- **Quality Gates** - 8-step validation pipeline
- **Session Lifecycle** - Event-driven session management

### SuperClaude-Lite

轻量级的

### V4 版本亮点

#### Behavioral Intelligence 行为智能

- **Automatic Mode Detection** - 根据上下文行为适应
- **Cross-Mode Coordination** - 行为模式之间的无缝集成
- **Progressive Enhancement** - 能力随复杂性而扩展

#### Agent Orchestration

- **Intelligent Routing** - 基于领域专业知识的 agents 的选择
- **Collaborative Problem-Solving** - 复杂任务的多 agents 协调
- **Context Preservation** - agents 在交互过程中保持意识

#### Session Management

- **Persistent Context** - 跨 session 的完整项目状态保存
- **Intelligent Checkpointing** - 根据风险和完成情况自动保存
- **Cross-Session Learning** - 积累的洞察力和模式识别

### Configuration

具有增强行为控制的 V4 配置：

- `~/.claude/settings.json` - Main V4 configuration with modes and agents
- `~/.claude/*.md` - Behavioral mode configurations
- `~/.claude/agents/` - Agent-specific customizations
- `~/.serena/` - Session lifecycle and memory management

## 21 Specialized Commands

### Development

**Development**: `/sc:implement`, `/sc:build`, `/sc:design`  

### Analysis

**Analysis**: `/sc:analyze`, `/sc:troubleshoot`, `/sc:explain`  

### Quality

**Quality**: `/sc:improve`, `/sc:test`, `/sc:cleanup`  

### Session

**Session**: `/sc:load`, `/sc:save`, `/sc:brainstorm`, `/sc:reflect`  

### Workflow

**Workflow**: `/sc:task`, `/sc:spawn`, `/sc:workflow`, `/sc:select-tool`  

### Others

**Others**: `/sc:document`, `/sc:git`, `/sc:estimate`, `/sc:index`
