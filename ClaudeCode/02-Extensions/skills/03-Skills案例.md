
# Claude Skills 使用

## anthropics 官方 Skills

<https://github.com/anthropics/skills>

```shell
/plugin marketplace add anthropics/skills
```

### Document Skills

处理复杂文件格式的技能：

- **[docx](https://github.com/anthropics/skills/tree/main/document-skills/docx)**  创建、编辑和分析 Word 文档，支持修订跟踪、批注、格式保留和文本提取
- **[pdf](https://github.com/anthropics/skills/tree/main/document-skills/pdf)**  全面的 PDF 处理工具包，可用于提取文本和表格、创建新 PDF、合并/拆分文档以及处理表单
- **[pptx](https://github.com/anthropics/skills/tree/main/document-skills/pptx)**  创建、编辑和分析 PowerPoint 演示文稿，支持版式、模板、图表以及自动幻灯片生成功能
- **[xlsx](https://github.com/anthropics/skills/tree/main/document-skills/xlsx)**  创建、编辑和分析 Excel 电子表格，支持公式、格式设置、数据分析和可视化

### Design & Creative

- **[algorithmic-art](https://github.com/anthropics/skills/tree/main/algorithmic-art)** - 使用 p 5. js 结合种子随机性、流场和粒子系统创作生成艺术
- **[canvas-design](https://github.com/anthropics/skills/tree/main/canvas-design)** - 运用设计理念，以. png 和. pdf 格式设计精美的视觉艺术作品
- **[slack-gif-creator](https://github.com/anthropics/skills/tree/main/slack-gif-creator)** - 创建针对 Slack 尺寸限制优化的动画 GIF

### Development

- **[artifacts-builder](https://github.com/anthropics/skills/tree/main/artifacts-builder)** - 使用 React、Tailwind CSS 和 shadcn/ui 组件构建复杂的 claude.ai HTML 制品
- **[mcp-builder](https://github.com/anthropics/skills/tree/main/mcp-builder)** - 创建高质量 MCP 服务器以集成外部 API 和服务的指南
- **[webapp-testing](https://github.com/anthropics/skills/tree/main/webapp-testing)** - 使用 Playwright 测试本地 Web 应用程序，以进行用户界面验证和调试

### Communication

- **[brand-guidelines](https://github.com/anthropics/skills/tree/main/brand-guidelines)** - Apply Anthropic's official brand colors and typography to artifacts 将 Anthropic 的官方品牌颜色和字体应用于成果物
- **[internal-comms](https://github.com/anthropics/skills/tree/main/internal-comms)** - Write internal communications like status reports, newsletters, and FAQs 撰写内部沟通内容，如状态报告、新闻通讯和常见问题解答

### Skill Creation

- **[skill-creator](https://github.com/anthropics/skills/tree/main/skill-creator)** 交互式技能创建工具，通过问答引导你构建新技能

## 三方 Skills

### Document Skills

#### Markdown to EPUB MD 转 EPUB

<https://mcpservers.org/claude-skills/smerchek/markdown-to-epub>

### Development

#### Playwright Skill by lackeyjb

<https://mcpservers.org/claude-skills/lackeyjb/playwright-skill>

### Productivity Skills

### Deep Reading Analyst 深度学习

<https://github.com/ginobefun/deep-reading-analyst-skill>

一个专业的 Claude AI 技能包，通过系统化的思维框架将表面阅读转化为深度学习。

> 常用的一些阅读方法打包成一个 Skil：有结构化思维、5W2H 分析、多元思维模型和逆向思维模型

### Skill_Seekers

<https://github.com/yusufkaraaslan/Skill_Seekers>

可以自动抓取文档网站、GitHub 仓库和 PDF 文件，并转换为 Claude 能直接使用的 Skill（技能包）

**主要功能：**
- 支持文档网站、GitHub 仓库、PDF 文件三种来源混合爬取；
- 自动检测文档与代码间的冲突并标注警告；
- 内置 Godot、React、Vue、Django 等 8 个常用框架预设；
- 深度代码分析，提取函数、类、方法及参数类型信息；
- 异步模式让爬取速度提升 2-3 倍；
- 本地 AI 增强功能，无需 API 费用即可生成完整指南。

**用途：** 学习新的知识，特别是小众的，新的技术

**安装：**
- MCP 方式

```shell
pip install skill-seekers

# MCP
# Clone repository
git clone https://github.com/yusufkaraaslan/Skill_Seekers.git
cd Skill_Seekers

# One-time setup (5 minutes)
./setup_mcp.sh

## python环境可能报错
# Create virtual environment
python3 -m venv .venv

# Activate virtual environment
source .venv/bin/activate  # macOS/Linux
# OR on Windows: venv\Scripts\activate

# Restart Claude Code, then just ask:
```

- CLI 方式

```shell
# Clone repository
git clone https://github.com/yusufkaraaslan/Skill_Seekers.git
cd Skill_Seekers

# Create virtual environment
python3 -m venv .venv

# Activate virtual environment
source .venv/bin/activate  # macOS/Linux
# OR on Windows: venv\Scripts\activate

# Install dependencies
pip install requests beautifulsoup4 pytest

# Save dependencies
pip freeze > requirements.txt

# Optional: Install anthropic for API-based enhancement (not needed for LOCAL enhancement)
# pip install anthropic
```

**Ref:**

[🚀程序员福音！学习新框架从此不用看文档？Skill Seeker让Claude成为你的技术导师，CrewAI、AutoGen、LangGraph随便上，自动生成完整项目代码，告别学习曲线陡峭的噩梦！不用再啃文档了！这个工具让 Claude 秒懂任何技术框架 - AI超元域的博客](https://www.aivi.fyi/aiagents/introduce-Skill-Seeker)

### Claude Code 调用其他 cli 工具

#### ClaudeCode 里使用 Codex 的 skill

**使用场景：** 在相对依赖上下文、ClaudeCode 自己的模型又解决不了问题的时候，可以直接说 " 让 Codex 解决这个问题 "。
**实现：**
是基于 codex mcp 实现的

Ref：

- <https://x.com/Stephen4171127/status/1990454842754846735?s=09>
- <https://github.com/foreveryh/Claude-Codex>

#### ClaudeCode 里使用 Gemini Cli 的 skill

- <https://github.com/forayconsulting/gemini_cli_skill>
- [Custom CC Skill for Gemini 3 Pro use via gemini-cli : r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1p0svbb/custom_cc_skill_for_gemini_3_pro_use_via_geminicli/)

## Skills 开源库和教程

### 教程

- [Claude Code Templates - Supercharge Your AI-Powered Development with Anthropic's Claude Code](https://www.aitmpl.com/skills)
- [自发布以来，我一直在跟踪人们使用 Claude Skills 构建的内容 - 这是我发现的最疯狂的东西（带有链接） : r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1o9ph4u/ive_been_tracking_what_people_are_building_with/?tl=zh-hans)

### 三方 skill 市场

<https://mcpservers.org/claude-skills>

<https://github.com/VoltAgent/awesome-claude-skills>

<https://github.com/travisvn/awesome-claude-skills>

<https://github.com/obra/superpowers>

<https://github.com/abubakarsiddik31/claude-skills-collection>

<https://github.com/ComposioHQ/awesome-claude-skills>

- Explore Claude Skills, And Generate Yours Featuring 175 Up-to-date Claude Skills
<https://skillshunt.io>

<https://skillsmp.com/zh>
