# Claude Code - Skills 完整说明文档

> Claude Code Skills 使用指南 | 扩展 AI 能力的 19 个专用工具

本文档汇总了所有可用 Skills 的详细说明,帮助你充分利用这些强大的 AI 扩展工具。

## 📚 目录

- [Skills 概览](#skills-概览)
- [文档处理 Skills](#文档处理-skills)
- [艺术与设计 Skills](#艺术与设计-skills)
- [前端 Web Skills](#前端-web-skills)
- [内容分析 Skills](#内容分析-skills)
- [开发工具 Skills](#开发工具-skills)
- [媒体处理 Skills](#媒体处理-skills)
- [使用技巧](#使用技巧)
- [最佳实践](#最佳实践)

---

## Skills 概览

### 按类别分类

| 类别 | Skills 数量 | 核心用途 |
|------|------------|---------|
| 📄 [文档处理](#文档处理-skills) | 5 | Word/PDF/Excel/PPT 文档操作 |
| 🎨 [艺术与设计](#艺术与设计-skills) | 3 | 生成式艺术、视觉设计、动画 |
| 🌐 [前端 Web](#前端-web-skills) | 3 | React 应用、主题定制、自动化测试 |
| 🔍 [内容分析](#内容分析-skills) | 3 | 深度阅读、MCP 开发、沟通文档 |
| ⚙️ [开发工具](#开发工具-skills) | 3 | Skill 开发、视频下载、模板 |
| 🎥 [媒体处理](#媒体处理-skills) | 2 | 品牌设计、源码追踪 |

**总 Skills 数**: 19 个

### 快速索引

| Skill | 类别 | 主要功能 | 推荐度 |
|-------|------|---------|--------|
| [docx](#docx-word-文档处理) | 文档 | Word 文档创建/编辑/批注 | ⭐⭐⭐⭐⭐ |
| [pdf](#pdf-pdf-文档操作) | 文档 | PDF 操作/表单填写/提取 | ⭐⭐⭐⭐⭐ |
| [xlsx](#xlsx-excel-表格处理) | 文档 | Excel 表格/公式/图表 | ⭐⭐⭐⭐⭐ |
| [pptx](#pptx-powerpoint-演示) | 文档 | PowerPoint 演示文稿 | ⭐⭐⭐⭐ |
| [pdf-processing-pro](#pdf-processing-pro-高级-pdf-处理) | 文档 | 高级 PDF 处理/OCR/批量 | ⭐⭐⭐⭐ |
| [algorithmic-art](#algorithmic-art-算法艺术) | 艺术 | p5.js 算法艺术/流场 | ⭐⭐⭐⭐ |
| [canvas-design](#canvas-design-视觉设计) | 艺术 | 视觉设计/海报/PNG/PDF | ⭐⭐⭐⭐ |
| [slack-gif-creator](#slack-gif-creator-slack-动画) | 艺术 | Slack 动画 GIF 创作 | ⭐⭐⭐ |
| [artifacts-builder](#artifacts-builder-复杂-web-应用) | Web | 复杂 React 应用构建 | ⭐⭐⭐⭐⭐ |
| [theme-factory](#theme-factory-主题定制) | Web | Artifacts 主题定制 | ⭐⭐⭐ |
| [webapp-testing](#webapp-testing-web-测试) | Web | Playwright 自动化测试 | ⭐⭐⭐⭐ |
| [deep-reading-analyst](#deep-reading-analyst-深度阅读) | 分析 | 深度阅读/批判性思考 | ⭐⭐⭐⭐⭐ |
| [mcp-builder](#mcp-builder-mcp-服务开发) | 分析 | MCP Server 开发 | ⭐⭐⭐⭐⭐ |
| [internal-comms](#internal-comms-内部沟通) | 分析 | 内部沟通文档 | ⭐⭐⭐ |
| [skill-creator](#skill-creator-skill-开发) | 开发 | 创建自定义 Skills | ⭐⭐⭐⭐⭐ |
| [video-downloader](#video-downloader-视频下载) | 开发 | YouTube 视频下载 | ⭐⭐⭐ |
| [template-skill](#template-skill-skill-模板) | 开发 | Skill 开发模板 | ⭐⭐⭐ |
| [brand-guidelines](#brand-guidelines-品牌规范) | 媒体 | Anthropic 品牌规范 | ⭐⭐⭐ |
| [source-tracing](#source-tracing-源码追踪) | 开发 | 源码追踪分析 | ⭐⭐⭐ |

---

## 文档处理 Skills

### docx - Word 文档处理

#### 💡 功能概述

完整的 Word 文档处理能力,支持文档创建、编辑、批注追踪和格式化。

**核心功能**:
- ✅ **创建文档** - 从零开始创建新的 Word 文档
- ✅ **编辑内容** - 修改现有文档的文字、段落、格式
- ✅ **追踪修订** - 添加批注和追踪文档修改历史
- ✅ **格式保留** - 完整保留文档的原始格式
- ✅ **文本提取** - 从 Word 文档中提取文本和数据

**技术特点**:
- 支持 `.docx` 格式
- 完整的格式化支持 (字体、段落、样式)
- 批注和修订追踪
- 表格和列表处理
- 图片和嵌入对象

#### 🎯 适用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 📄 技术文档 | 创建技术规格、API 文档 | "使用 docx skill 创建 API 设计文档" |
| ✍️ 合同编辑 | 编辑法律文件和合同 | "使用 docx skill 在合同第 5 段添加批注" |
| 💬 协作审阅 | 添加审阅批注和建议 | "使用 docx skill 对文档进行审阅并添加批注" |
| 🔄 版本管理 | 追踪文档修订历史 | "使用 docx skill 查看文档的修订历史" |
| 📊 数据提取 | 从 Word 提取表格数据 | "使用 docx skill 提取文档中的所有表格" |

#### 📖 使用示例

```python
# 示例 1: 创建新文档
使用 docx skill 创建一份技术规格文档,包含标题、章节和表格

# 示例 2: 编辑现有文档
使用 docx skill 在文档第 3 段添加批注:"需要补充性能指标"

# 示例 3: 提取内容
使用 docx skill 提取文档中的所有代码块和示例

# 示例 4: 格式化
使用 docx skill 将所有代码示例设置为等宽字体
```

---

### pdf - PDF 文档操作

#### 💡 功能概述

PDF 文档操作工具,支持表单填写、文本提取、页面合并分割等常用 PDF 操作。

**核心功能**:
- ✅ **表单填写** - 自动填写 PDF 表单字段
- ✅ **文本提取** - 从 PDF 提取文本内容
- ✅ **表格提取** - 识别并提取 PDF 中的表格数据
- ✅ **合并/分割** - 合并多个 PDF 或分割大型文档
- ✅ **页面操作** - 旋转、删除、重排 PDF 页面
- ✅ **水印添加** - 为 PDF 添加文字或图片水印

**技术特点**:
- 表单自动识别和填充
- 高精度文本提取
- 表格结构识别
- 页面级别操作
- 批量处理支持

#### 🎯 适用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 📝 表单填写 | 自动填写申请表、合同 | "使用 pdf skill 填写签证申请表" |
| 🔍 内容提取 | 提取 PDF 中的文本和数据 | "使用 pdf skill 提取报告中的所有数据表" |
| 🔗 文档合并 | 合并多个 PDF 为一个 | "使用 pdf skill 合并所有月度报告" |
| ✂️ 文档分割 | 将大 PDF 拆分为多个小文件 | "使用 pdf skill 将手册按章节分割" |
| 🔄 页面重排 | 调整 PDF 页面顺序 | "使用 pdf skill 将第 10 页移到第 2 页" |

#### 📖 使用示例

```python
# 示例 1: 填写表单
使用 pdf skill 填写 application_form.pdf 中的所有字段

# 示例 2: 提取数据
使用 pdf skill 从 financial_report.pdf 提取所有表格数据到 CSV

# 示例 3: 合并文档
使用 pdf skill 合并 doc1.pdf, doc2.pdf, doc3.pdf 为 combined.pdf

# 示例 4: 分割文档
使用 pdf skill 将 large_manual.pdf 的每 10 页分割为一个文件

# 示例 5: 添加水印
使用 pdf skill 为 contract.pdf 添加"机密"水印
```

---

### xlsx - Excel 表格处理

#### 💡 功能概述

Excel 表格处理工具,支持创建、编辑、公式计算和数据可视化。

**核心功能**:
- ✅ **创建表格** - 创建新的 Excel 工作簿和工作表
- ✅ **数据编辑** - 编辑单元格数据和格式
- ✅ **公式计算** - 创建和重新计算 Excel 公式
- ✅ **图表生成** - 生成各种类型的数据图表
- ✅ **数据透视表** - 创建和配置数据透视表
- ✅ **样式格式化** - 设置单元格样式、颜色、边框
- ✅ **数据分析** - 排序、筛选、统计分析

**支持格式**:
- `.xlsx` (Excel 2007+)
- `.xlsm` (启用宏的 Excel)
- `.csv` (逗号分隔值)
- `.tsv` (制表符分隔值)

#### 🎯 适用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 📊 数据分析 | 统计分析和数据处理 | "使用 xlsx skill 分析销售数据并计算增长率" |
| 📈 图表生成 | 创建可视化图表 | "使用 xlsx skill 生成月度趋势图" |
| 🧮 公式计算 | 复杂公式和函数 | "使用 xlsx skill 计算 VLOOKUP 和 SUMIF" |
| 📋 报表生成 | 自动化生成报表 | "使用 xlsx skill 生成季度财务报表" |
| 🔄 数据透视 | 数据透视表分析 | "使用 xlsx skill 创建销售数据透视表" |

#### 📖 使用示例

```python
# 示例 1: 创建报表
使用 xlsx skill 创建销售数据分析报表,包含:
- 原始数据表
- 月度汇总表
- 趋势图表
- 数据透视表

# 示例 2: 公式计算
使用 xlsx skill 在表格中添加以下公式:
- 列 D: 增长率 = (本月 - 上月) / 上月
- 列 E: 累计值 = SUM($C$2:C2)

# 示例 3: 图表生成
使用 xlsx skill 为数据生成:
- 柱状图 (销售额对比)
- 折线图 (趋势变化)
- 饼图 (市场份额)

# 示例 4: 数据分析
使用 xlsx skill 对数据进行:
- 按销售额降序排序
- 筛选出销售额 > 100000 的记录
- 计算平均值、中位数、标准差

# 示例 5: 格式化
使用 xlsx skill 设置表格样式:
- 标题行:粗体、背景色
- 数据行:交替行背景色
- 数字:千位分隔符
```

---

### pptx - PowerPoint 演示

#### 💡 功能概述

PowerPoint 演示文稿处理工具,支持创建、编辑幻灯片和布局定制。

**核心功能**:
- ✅ **创建演示** - 创建新的 PowerPoint 演示文稿
- ✅ **编辑幻灯片** - 修改幻灯片内容和布局
- ✅ **布局定制** - 自定义幻灯片布局和主题
- ✅ **添加备注** - 为幻灯片添加演讲者备注
- ✅ **批注管理** - 添加和管理审阅批注
- ✅ **格式保留** - 保留演示文稿的原始格式

**技术特点**:
- 支持 `.pptx` 格式
- 完整的布局系统
- 主题和样式管理
- 演讲者备注
- 动画和过渡效果

#### 🎯 适用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 🎤 技术演讲 | 创建技术分享 PPT | "使用 pptx skill 创建 AI 技术分享 PPT" |
| 📊 数据展示 | 制作数据展示幻灯片 | "使用 pptx skill 制作季度业绩汇报" |
| 📝 编辑修改 | 更新现有演示文稿 | "使用 pptx skill 更新第 5 页的数据图表" |
| 💬 审阅协作 | 添加审阅批注 | "使用 pptx skill 对演示稿添加修改建议" |

#### 📖 使用示例

```python
# 示例 1: 创建演示
使用 pptx skill 创建项目进度汇报 PPT,包含:
- 标题页
- 目录页
- 进度概览 (文字+图表)
- 关键成果展示
- 下一步计划
- 总结页

# 示例 2: 编辑幻灯片
使用 pptx skill 修改第 3 页:
- 更新销售数据为最新数字
- 调整图表配色方案
- 添加趋势说明文字

# 示例 3: 添加备注
使用 pptx skill 为每页幻灯片添加演讲者备注

# 示例 4: 布局调整
使用 pptx skill 统一调整所有幻灯片的布局和主题颜色
```

---

### pdf-processing-pro - 高级 PDF 处理

#### 💡 功能概述

高级 PDF 处理工具,支持 OCR、批量操作、表单处理和生产级 PDF 工作流。

**核心功能**:
- ✅ **OCR 识别** - 光学字符识别,提取扫描件文字
- ✅ **批量处理** - 批量操作大量 PDF 文件
- ✅ **高级表单** - 复杂表单识别和填充
- ✅ **PDF 验证** - 文件完整性和格式验证
- ✅ **错误处理** - 强大的错误处理和恢复机制
- ✅ **生产工作流** - 企业级 PDF 处理流程

**技术特点**:
- Tesseract OCR 引擎
- 并行批量处理
- 表单字段智能识别
- PDF/A 标准支持
- 详细的处理日志

#### 🎯 适用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 🔍 扫描件 OCR | 识别扫描文档中的文字 | "使用 pdf-processing-pro skill 对 100 个扫描发票进行 OCR" |
| ⚙️ 批量处理 | 批量操作大量 PDF | "使用 pdf-processing-pro skill 批量提取所有 PDF 的表格数据" |
| ✅ 文件验证 | 验证 PDF 文件完整性 | "使用 pdf-processing-pro skill 验证 PDF 文件符合 PDF/A 标准" |
| 🏭 生产环境 | 企业级 PDF 处理 | "使用 pdf-processing-pro skill 构建发票自动化处理流程" |

#### 📖 使用示例

```python
# 示例 1: OCR 识别
使用 pdf-processing-pro skill 对扫描的合同文件进行 OCR,并提取关键信息:
- 合同编号
- 签约日期
- 合同金额
- 签约方信息

# 示例 2: 批量提取
使用 pdf-processing-pro skill 批量处理 500 个 PDF 文件:
- 提取每个文件的表格数据
- 验证数据完整性
- 汇总到一个 Excel 文件

# 示例 3: 表单批量填写
使用 pdf-processing-pro skill 批量填写 100 份申请表单

# 示例 4: PDF 验证
使用 pdf-processing-pro skill 验证所有 PDF 文件:
- 检查文件损坏
- 验证 PDF/A 合规性
- 生成验证报告
```

---

## 艺术与设计 Skills

### algorithmic-art - 算法艺术

#### 💡 功能概述

使用 p5.js 创建生成式算法艺术,支持流场、粒子系统和交互式参数探索。

**核心功能**:
- ✅ **算法哲学** - 创建艺术生成的核心算法思想
- ✅ **p5.js 实现** - 将算法转换为可视化艺术
- ✅ **流场可视化** - 创建复杂的流场图案
- ✅ **粒子系统** - 模拟粒子运动和交互
- ✅ **种子随机性** - 使用种子确保艺术可重现
- ✅ **参数控制** - 交互式调整艺术参数

**技术特点**:
- 两步流程: 算法哲学 → p5.js 实现
- 基于 `templates/viewer.html`
- Anthropic 品牌一致性
- 参数化设计支持探索

#### 🎯 适用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 🎨 算法艺术 | 创作生成式艺术作品 | "使用 algorithmic-art skill 创建佩林噪声流场" |
| 🌊 流场可视化 | 可视化复杂流场 | "使用 algorithmic-art skill 创建向量场可视化" |
| ✨ 粒子效果 | 粒子系统动画 | "使用 algorithmic-art skill 生成星空粒子效果" |
| 🎮 交互艺术 | 创建交互式艺术 | "使用 algorithmic-art skill 创建鼠标交互的流体效果" |

#### 📖 使用示例

```javascript
// 示例 1: 流场艺术
使用 algorithmic-art skill 创建一个佩林噪声流场可视化:
- 使用 Perlin Noise 生成流场
- 粒子沿流场运动并留下轨迹
- 可调整噪声缩放和粒子数量
- 使用 Anthropic 品牌配色

// 示例 2: 生成树
使用 algorithmic-art skill 创建分形树生成:
- 递归绘制树枝
- 随机角度和长度变化
- 种子控制确保可重现
- 参数:角度、深度、缩放比

// 示例 3: 粒子星空
使用 algorithmic-art skill 生成交互式星空:
- 数千粒子随机分布
- 鼠标吸引/排斥效果
- 粒子间连线形成星座
- 平滑动画和过渡
```

---

### canvas-design - 视觉设计

#### 💡 功能概述

创建专业级视觉设计,生成 PNG 和 PDF 格式的海报、艺术作品和设计图。

**核心功能**:
- ✅ **海报设计** - 创建活动海报、宣传图
- ✅ **视觉艺术** - 创作数字艺术作品
- ✅ **PNG/PDF 输出** - 导出高质量图片和文档
- ✅ **设计哲学** - 遵循设计原则和美学

**设计原则**:
- 创建原创视觉设计
- 不复制现有艺术家作品
- 注重排版和色彩理论
- 平衡美学和功能性

#### 🎯 适用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 📄 技术海报 | 设计技术活动海报 | "使用 canvas-design skill 设计 AI 技术大会海报" |
| 🎨 艺术创作 | 创作抽象艺术 | "使用 canvas-design skill 创作几何抽象艺术" |
| 🖼️ 宣传物料 | 制作宣传图片 | "使用 canvas-design skill 设计产品宣传图" |

#### 📖 使用示例

```python
# 示例 1: 技术海报
使用 canvas-design skill 设计一个技术大会的海报:
- 标题: "AI 前沿技术峰会 2025"
- 视觉元素: 抽象的神经网络图案
- 配色: 科技感蓝色渐变
- 包含: 日期、地点、主办方信息
- 输出: PNG (1080x1920) 和 PDF

# 示例 2: 抽象艺术
使用 canvas-design skill 创作几何抽象艺术:
- 主题: 数据可视化的美学
- 元素: 圆形、三角形、线条的组合
- 配色: 协调的三色调色板
- 风格: 现代主义、极简
- 输出: 高分辨率 PNG

# 示例 3: 信息图表
使用 canvas-design skill 设计信息图表:
- 主题: 机器学习发展历程
- 布局: 时间线形式
- 包含: 关键事件、里程碑、插图
- 输出: PNG 和 PDF 格式
```

---

### slack-gif-creator - Slack 动画

#### 💡 功能概述

为 Slack 创建优化的动画 GIF,支持尺寸约束和动画组合。

**核心功能**:
- ✅ **GIF 动画** - 创建循环播放的 GIF 动画
- ✅ **Slack 优化** - 符合 Slack 的尺寸限制
- ✅ **动画效果** - 多种动画效果组合
- ✅ **文件大小控制** - 自动优化文件大小
- ✅ **尺寸验证** - 验证符合 Slack emoji 标准

**技术约束**:
- 最大尺寸: 128KB
- 推荐分辨率: 128x128
- 帧率优化
- 颜色优化减小文件

#### 🎯 适用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 💬 Slack 表情 | 创建团队专属 emoji | "使用 slack-gif-creator skill 创建庆祝动画 emoji" |
| 🎬 反馈动画 | 制作反馈动画 | "使用 slack-gif-creator skill 创建"正在审查"动画" |
| 🎭 团队文化 | 团队专属动画表情 | "使用 slack-gif-creator skill 制作团队吉祥物动画" |

#### 📖 使用示例

```python
# 示例 1: 庆祝动画
使用 slack-gif-creator skill 创建一个庆祝成功的 GIF:
- 动画: 奖杯从下方升起并闪光
- 尺寸: 128x128
- 帧数: 20 帧
- 循环播放
- 文件大小: < 128KB

# 示例 2: 加载动画
使用 slack-gif-creator skill 创建"正在处理"加载动画:
- 动画: 三个点依次跳动
- 颜色: Slack 绿色
- 简洁循环
- 文件优化

# 示例 3: 反馈表情
使用 slack-gif-creator skill 创建点赞动画:
- 大拇指从小到大再缩小
- 配合星光效果
- 平滑动画过渡
```

---

## 前端 Web Skills

### artifacts-builder - 复杂 Web 应用

#### 💡 功能概述

构建复杂的 claude.ai HTML artifacts,使用现代前端技术 (React、Tailwind CSS、shadcn/ui)。

**核心技术栈**:
- ⚛️ **React** - 现代化的 UI 组件库
- 🎨 **Tailwind CSS** - 实用优先的 CSS 框架
- 🧩 **shadcn/ui** - 高质量 React 组件
- 🔄 **状态管理** - React Hooks 和 Context
- 🚦 **路由系统** - 客户端路由

**适用类型**:
- ✅ 需要状态管理的复杂应用
- ✅ 多页面应用 (需要路由)
- ✅ 使用 shadcn/ui 组件的应用

**不适用**:
- ❌ 简单的单文件 HTML/JSX artifacts

#### 🎯 适用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 🚀 复杂应用 | 构建多功能 Web 应用 | "使用 artifacts-builder skill 创建任务管理应用" |
| 🎨 组件库 | 使用 shadcn/ui 组件 | "使用 artifacts-builder skill 构建使用 shadcn/ui 的仪表板" |
| 🔄 状态管理 | 需要复杂状态管理 | "使用 artifacts-builder skill 创建购物车应用" |

#### 📖 使用示例

```jsx
// 示例 1: 任务管理应用
使用 artifacts-builder skill 创建一个待办事项应用:
- 功能: 添加、编辑、删除、标记完成任务
- 组件: shadcn/ui 的 Button、Input、Checkbox、Dialog
- 状态: React Context 管理任务列表
- 样式: Tailwind CSS
- 持久化: localStorage

// 示例 2: 数据可视化仪表板
使用 artifacts-builder skill 构建数据仪表板:
- 多个图表展示 (使用 Recharts)
- 过滤和搜索功能
- shadcn/ui 的 Card、Tabs、Select 组件
- 响应式布局 (Tailwind)
- 数据刷新机制

// 示例 3: 交互式表单
使用 artifacts-builder skill 创建多步骤表单:
- 多步向导界面
- 表单验证 (React Hook Form)
- shadcn/ui 的 Form 组件
- 进度指示器
- 数据预览和提交
```

---

### theme-factory - 主题定制

#### 💡 功能概述

为 artifacts 应用预设主题样式,提供 10 种预设主题和自定义主题生成。

**核心功能**:
- ✅ **10 种预设主题** - 开箱即用的配色方案
- ✅ **自定义主题** - 即时生成新主题
- ✅ **颜色配置** - 主色、辅色、背景色配置
- ✅ **字体配置** - 字体族、大小、行高配置
- ✅ **实时预览** - 主题效果实时查看

**预设主题包括**:
- 浅色主题 (Light)
- 深色主题 (Dark)
- 蓝色科技 (Tech Blue)
- 绿色自然 (Nature Green)
- 紫色典雅 (Elegant Purple)
- 等...

#### 🎯 适用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 🎨 快速主题 | 应用预设主题 | "使用 theme-factory skill 为应用应用深色主题" |
| 🌈 自定义配色 | 创建品牌配色 | "使用 theme-factory skill 创建蓝色科技风主题" |
| 📱 统一风格 | 统一多个 artifact 风格 | "使用 theme-factory skill 为所有仪表板应用同一主题" |

#### 📖 使用示例

```css
// 示例 1: 应用预设主题
使用 theme-factory skill 为应用应用深色主题

// 示例 2: 创建自定义主题
使用 theme-factory skill 创建一个主题:
- 主色: #3B82F6 (蓝色)
- 辅色: #10B981 (绿色)
- 背景: #F9FAFB (浅灰)
- 文字: #111827 (深灰)
- 字体: Inter, system-ui

// 示例 3: 主题变体
使用 theme-factory skill 基于现有主题创建变体:
- 基础: Tech Blue
- 调整: 增加对比度、调整圆角半径
```

---

### webapp-testing - Web 测试

#### 💡 功能概述

使用 Playwright 进行 Web 应用自动化测试,支持功能验证、UI 调试和截图。

**核心功能**:
- ✅ **Playwright 自动化** - 强大的浏览器自动化
- ✅ **功能测试** - 验证前端功能正确性
- ✅ **UI 调试** - 调试 UI 行为和交互
- ✅ **截图捕获** - 捕获页面截图
- ✅ **日志查看** - 查看浏览器控制台日志
- ✅ **交互模拟** - 模拟用户点击、输入等操作

**技术特点**:
- 支持 Chrome、Firefox、Safari
- 异步操作支持
- 元素选择器
- 等待条件
- 视觉回归测试

#### 🎯 适用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 🧪 功能测试 | 测试 Web 应用功能 | "使用 webapp-testing skill 测试登录表单功能" |
| 🐛 UI 调试 | 调试 UI 交互问题 | "使用 webapp-testing skill 调试下拉菜单行为" |
| 📸 视觉测试 | 截图对比测试 | "使用 webapp-testing skill 捕获页面截图进行对比" |

#### 📖 使用示例

```javascript
// 示例 1: 登录功能测试
使用 webapp-testing skill 测试登录表单:
- 访问 http://localhost:3000/login
- 输入用户名和密码
- 点击登录按钮
- 验证重定向到首页
- 检查用户名显示正确

// 示例 2: 表单验证测试
使用 webapp-testing skill 测试表单验证:
- 提交空表单,验证错误提示
- 输入无效邮箱,验证格式错误提示
- 输入过短密码,验证长度限制提示

// 示例 3: 截图对比
使用 webapp-testing skill 进行视觉回归测试:
- 捕获当前页面截图
- 与基准截图对比
- 标注差异区域
- 生成对比报告
```

---

## 内容分析 Skills

### deep-reading-analyst - 深度阅读

#### 💡 功能概述

深度阅读分析工具,使用多种思维模型 (结构化思考、第一性原理、批判性思维等) 分析长文。

**思维框架 (10+ 种)**:
- 📊 **SCQA** - 情境-冲突-问题-答案
- 🔍 **5W2H** - 何人何时何地何事为何如何多少
- 🧠 **批判性思维** - 逻辑谬误识别
- 🔄 **逆向思维** - 反向假设推理
- 🎯 **心智模型** - 底层原理理解
- ⚛️ **第一性原理** - 从基本事实推导
- 🌐 **系统思维** - 整体和关联分析
- 🎨 **六顶思考帽** - 多角色视角
- 📈 **SWOT** - 优劣势机会威胁
- 🔬 **PEST** - 政治经济社会技术分析

**分析深度级别**:
- ⚡ **快速分析** (15 分钟) - SCQA + 5W2H
- 📝 **标准分析** (30 分钟) - + 批判性思维 + 逆向思维
- 🔬 **深度分析** (60 分钟) - + 心智模型 + 第一性原理 + 系统思维 + 六顶思考帽
- 📚 **研究分析** (120 分钟+) - + 跨来源比较

#### 🎯 适用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 📚 深度理解 | 理解复杂技术文章 | "使用 deep-reading-analyst skill 分析这篇关于 Transformer 的论文" |
| 🔍 论文分析 | 分析学术论文 | "使用 deep-reading-analyst skill 用第一性原理分析这篇论文" |
| 💡 提取洞察 | 提取可行洞察 | "使用 deep-reading-analyst skill 从这篇文章提取实践建议" |
| 📝 学习总结 | 创建学习笔记 | "使用 deep-reading-analyst skill 创建这篇教程的学习总结" |
| 🔬 对比研究 | 对比多个来源 | "使用 deep-reading-analyst skill 对比 3 篇关于 React 的文章" |

#### 📖 使用示例

```python
# 示例 1: 快速分析文章
使用 deep-reading-analyst skill 快速分析这篇技术博客:
- 框架: SCQA + 5W2H
- 时长: 15 分钟
- 输出: 文章摘要、关键要点、行动建议

# 示例 2: 深度分析论文
使用 deep-reading-analyst skill 深度分析 Attention Is All You Need 论文:
- 框架: 第一性原理 + 系统思维 + 批判性思维
- 时长: 60 分钟
- 输出:
  - 核心创新点分析
  - 技术实现原理
  - 优势和局限
  - 实践应用指导

# 示例 3: 对比研究
使用 deep-reading-analyst skill 对比分析 3 篇关于微服务架构的文章:
- 框架: 系统思维 + SWOT + 六顶思考帽
- 提取共同观点和分歧点
- 评估不同观点的优劣
- 综合形成自己的理解

# 示例 4: 提取可行建议
使用 deep-reading-analyst skill 从长文中提取实践建议:
- 框架: 5W2H + 心智模型
- 识别理论和实践的对应
- 提取可立即执行的步骤
- 按优先级排序建议
```

---

### mcp-builder - MCP 服务开发

#### 💡 功能概述

创建高质量 MCP (Model Context Protocol) 服务器,集成外部 API 和服务。

**核心流程** (4 步):
1. **深度研究和规划** - 理解需求和设计 MCP 工具
2. **实施** - 编写 MCP Server 代码
3. **审查和改进** - 代码审查和优化
4. **创建评估** - 测试和文档

**支持语言**:
- 🐍 **Python** - 使用 FastMCP 框架
- 📘 **TypeScript/Node.js** - 使用 MCP SDK

**设计原则**:
- 🔄 **为工作流构建** - 而非仅仅 API 端点
- 📊 **优化有限上下文** - 最小化 token 使用
- ⚠️ **可操作错误** - 清晰的错误消息
- 🧩 **自然任务细分** - 遵循任务逻辑分解

#### 🎯 适用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 🔧 创建 MCP | 开发新的 MCP Server | "使用 mcp-builder skill 创建天气查询 MCP Server" |
| 🔌 API 集成 | 集成外部服务 | "使用 mcp-builder skill 将 GitHub API 集成为 MCP 工具" |
| 🛠️ 扩展功能 | 扩展 Claude Code | "使用 mcp-builder skill 创建数据库查询 MCP 工具" |

#### 📖 使用示例

```python
# 示例 1: 天气查询 MCP (Python/FastMCP)
使用 mcp-builder skill 创建天气查询 MCP Server:
- 工具: get_weather(location: str) -> Weather
- 集成: OpenWeatherMap API
- 功能:
  - 查询当前天气
  - 7 天预报
  - 多地点对比
- 错误处理: API 失败、无效地点

# 示例 2: GitHub 集成 MCP (TypeScript)
使用 mcp-builder skill 将 GitHub API 集成为 MCP:
- 工具:
  - list_repos(user: string)
  - get_repo_info(owner: string, repo: string)
  - create_issue(repo: string, title: string, body: string)
  - search_code(query: string)
- 认证: GitHub Token
- 分页处理
- 速率限制处理

# 示例 3: 数据库查询 MCP
使用 mcp-builder skill 创建数据库查询 MCP:
- 支持: PostgreSQL, MySQL
- 工具:
  - query_schema() - 获取表结构
  - execute_query(sql: string) - 执行只读查询
  - get_table_stats(table: string) - 表统计信息
- 安全: 只读权限、SQL 注入防护
- 优化: 查询结果限制、缓存
```

---

### internal-comms - 内部沟通

#### 💡 功能概述

帮助撰写各种内部沟通文档,使用公司标准格式。

**支持文档类型**:
- 📊 **状态报告** - 项目进度状态更新
- 📢 **领导层更新** - 向领导汇报的简报
- 🔄 **3P 更新** - 第三方合作更新
- 📰 **公司新闻** - 内部新闻简报
- ❓ **FAQ 文档** - 常见问题解答
- 🚨 **事件报告** - 问题和事件报告
- 📋 **项目更新** - 项目进展通报

**文档特点**:
- 标准化格式
- 清晰的信息层次
- 适当的正式程度
- 针对受众优化

#### 🎯 适用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 📊 状态报告 | 撰写项目状态 | "使用 internal-comms skill 撰写本周项目状态报告" |
| 📢 领导沟通 | 向领导汇报 | "使用 internal-comms skill 创建季度总结汇报" |
| ❓ FAQ 创建 | 创建 FAQ 文档 | "使用 internal-comms skill 创建新功能的 FAQ" |

#### 📖 使用示例

```markdown
# 示例 1: 项目状态报告
使用 internal-comms skill 撰写本周项目状态报告:
- 项目名称: 用户认证系统升级
- 进展概况: 70% 完成
- 本周完成:
  - OAuth2 集成完成
  - 单元测试覆盖率达 90%
- 下周计划:
  - 完成集成测试
  - 开始安全审计
- 风险和问题:
  - 第三方 API 偶尔超时
  - 需要额外的安全审查时间

# 示例 2: FAQ 文档
使用 internal-comms skill 创建新功能的 FAQ:
- 功能: AI 代码审查助手
- FAQ 包含:
  - 什么是 AI 代码审查?
  - 如何启用这个功能?
  - 支持哪些编程语言?
  - 审查建议如何应用?
  - 数据隐私如何保障?
  - 遇到问题如何反馈?

# 示例 3: 事件报告
使用 internal-comms skill 撰写事件报告:
- 事件: API 服务中断 2 小时
- 时间线:
  - 14:00 - 用户开始报告错误
  - 14:15 - 团队开始调查
  - 15:30 - 发现根本原因
  - 16:00 - 服务恢复
- 根本原因: 数据库连接池耗尽
- 解决方案: 增加连接池大小
- 预防措施:
  - 改进监控告警
  - 添加自动扩容
  - 更新运维文档
```

---

## 开发工具 Skills

### skill-creator - Skill 开发

#### 💡 功能概述

创建和更新自定义 Claude Code Skills 的指导工具。

**开发流程** (6 步):
1. **通过示例理解** - 学习 skill 工作原理
2. **规划可重用内容** - 设计 skill 结构
3. **初始化 skill** - 运行 `scripts/init_skill.py`
4. **编辑 skill** - 编写 skill.md 和其他文件
5. **打包 skill** - 运行 `scripts/package_skill.py`
6. **迭代改进** - 测试和完善

**Skill 结构**:
```
my-skill/
├── skill.md           # 主要 skill 定义
├── templates/         # 模板文件 (可选)
├── examples/          # 示例代码 (可选)
└── README.md          # 文档 (可选)
```

**最佳实践**:
- ✅ 专注单一功能
- ✅ 提供清晰示例
- ✅ 详细文档说明
- ✅ 考虑错误处理

#### 🎯 适用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 🔨 创建 Skill | 开发新的 Skill | "使用 skill-creator skill 创建代码审查 Skill" |
| 🔄 更新 Skill | 更新现有 Skill | "使用 skill-creator skill 为 docx skill 添加新功能" |
| 📖 学习开发 | 学习 Skill 开发 | "使用 skill-creator skill 学习如何创建 Skill" |

#### 📖 使用示例

```python
# 示例 1: 创建代码审查 Skill
使用 skill-creator skill 创建一个代码审查 Skill:
- Skill 名称: code-reviewer
- 功能:
  - 检查代码风格
  - 识别潜在 bug
  - 建议改进方案
  - 生成审查报告
- 支持语言: Python, JavaScript, TypeScript
- 输出格式: Markdown 报告

# 示例 2: 更新 docx Skill
使用 skill-creator skill 为 docx skill 添加以下功能:
- 支持文档比较 (diff)
- 提取文档元数据
- 批量文档处理
- 文档模板应用

# 示例 3: 创建数据库迁移 Skill
使用 skill-creator skill 创建数据库迁移 Skill:
- 功能:
  - 生成迁移脚本
  - 执行迁移
  - 回滚迁移
  - 迁移状态查询
- 支持: PostgreSQL, MySQL, SQLite
- 安全检查: 备份提醒、破坏性操作确认
```

---

### video-downloader - 视频下载

#### 💡 功能概述

从 YouTube 等平台下载视频,支持多种格式和质量选项。

**核心功能**:
- ✅ **YouTube 下载** - 下载 YouTube 视频
- ✅ **格式选择** - 多种视频格式支持
- ✅ **质量选择** - 选择视频分辨率和质量
- ✅ **离线观看** - 下载后离线观看
- ✅ **字幕下载** - 下载视频字幕 (如有)

**支持平台**:
- YouTube
- Vimeo
- Dailymotion
- 等...

**格式支持**:
- MP4
- WEBM
- MKV
- 音频: MP3, M4A

#### 🎯 适用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 📹 教程下载 | 下载技术教程视频 | "使用 video-downloader skill 下载这个 Python 教程" |
| 💾 视频归档 | 保存重要视频 | "使用 video-downloader skill 批量下载会议录像" |
| ✂️ 素材获取 | 获取视频素材 | "使用 video-downloader skill 下载演示视频片段" |

#### 📖 使用示例

```bash
# 示例 1: 下载单个视频
使用 video-downloader skill 下载这个 YouTube 教程视频:
- URL: https://youtube.com/watch?v=xxxxx
- 质量: 1080p
- 格式: MP4
- 包含字幕

# 示例 2: 批量下载
使用 video-downloader skill 批量下载播放列表:
- 播放列表: Python 进阶教程系列
- 质量: 最高可用
- 保存到: ./tutorials/

# 示例 3: 下载音频
使用 video-downloader skill 仅下载视频音频:
- 格式: MP3
- 质量: 320kbps
- 用途: 播客离线收听
```

---

### template-skill - Skill 模板

#### 💡 功能概述

Skill 开发的模板和起点。

**用途**:
- 🚀 快速开始 Skill 开发
- 📋 参考 Skill 结构
- 📖 学习 Skill 开发规范

**包含内容**:
- Skill 基本结构
- 示例代码
- 文档模板

---

### source-tracing - 源码追踪

#### 💡 功能概述

源码追踪和分析工具。

**核心功能**:
- ✅ **代码溯源** - 追踪代码来源和历史
- ✅ **依赖分析** - 分析代码依赖关系

**适用场景**:
- 🔍 追踪代码来源
- 🕸️ 分析代码依赖
- 📊 理解代码演化

---

## 媒体处理 Skills

### brand-guidelines - 品牌规范

#### 💡 功能概述

应用 Anthropic 官方品牌颜色和字体到 artifacts。

**核心功能**:
- ✅ **Anthropic 品牌色** - 官方配色方案
- ✅ **官方字体** - 品牌字体规范
- ✅ **设计标准** - 视觉设计标准

**品牌元素**:
- 主色调
- 辅助色
- 字体族
- 排版规则
- 图标风格

#### 🎯 适用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 🎨 品牌风格 | 应用 Anthropic 品牌 | "使用 brand-guidelines skill 应用 Anthropic 品牌配色" |
| 📐 设计规范 | 遵循设计标准 | "使用 brand-guidelines skill 确保设计符合品牌规范" |

#### 📖 使用示例

```css
// 示例: 应用品牌配色
使用 brand-guidelines skill 为演示文稿应用 Anthropic 品牌风格:
- 主色: Anthropic 橙色
- 背景: 官方白色
- 文字: 品牌深灰色
- 字体: 官方字体族
- 图标: 品牌图标风格
```

---

## 使用技巧

### 💡 技巧 1: 组合使用 Skills

**文档工作流**:

```python
# 1. 深度阅读分析
使用 deep-reading-analyst skill 分析技术资料

# 2. 创建 Word 文档
使用 docx skill 创建技术文档

# 3. 制作 PowerPoint
使用 pptx skill 制作演示文稿

# 4. 生成可视化
使用 canvas-design skill 创建信息图表
```

---

### 💡 技巧 2: 批量操作

**批量 PDF 处理**:

```python
# 使用 pdf-processing-pro
使用 pdf-processing-pro skill 批量处理 100 个 PDF:
- OCR 识别扫描件
- 提取表格数据
- 验证文件完整性
- 生成汇总报告
```

---

### 💡 技巧 3: 开发工作流

**MCP 开发流程**:

```python
# 1. 创建 MCP Server
使用 mcp-builder skill 创建 weather MCP

# 2. 创建配套 Skill
使用 skill-creator skill 创建 weather skill

# 3. 测试 Web 应用
使用 webapp-testing skill 测试集成
```

---

### 💡 技巧 4: 自动化报告

**定期报告自动化**:

```python
# 1. 数据分析
使用 xlsx skill 分析月度数据

# 2. 生成图表
使用 canvas-design skill 创建可视化图表

# 3. 创建演示
使用 pptx skill 生成汇报 PPT

# 4. 撰写邮件
使用 internal-comms skill 撰写通报邮件
```

---

### 💡 技巧 5: 学习和知识管理

**学习工作流**:

```python
# 1. 深度阅读
使用 deep-reading-analyst skill 分析技术文章

# 2. 下载教程
使用 video-downloader skill 下载相关教程视频

# 3. 创建笔记
使用 docx skill 创建学习笔记文档

# 4. 制作演示
使用 pptx skill 制作知识分享 PPT
```

---

## 最佳实践

### ✅ 推荐做法

#### 1. 选择合适的 Skill

**文档操作**:
- Word 文档 → `docx` skill
- PDF 文档 → `pdf` 或 `pdf-processing-pro` skill
- PowerPoint → `pptx` skill
- Excel → `xlsx` skill

**创意设计**:
- 算法艺术 → `algorithmic-art` skill
- 静态设计 → `canvas-design` skill
- 复杂 Web 应用 → `artifacts-builder` skill
- Slack 动图 → `slack-gif-creator` skill

**分析和学习**:
- 深度阅读 → `deep-reading-analyst` skill
- 多种思维框架结合使用

**技术开发**:
- MCP 服务 → `mcp-builder` skill
- Web 测试 → `webapp-testing` skill
- Skill 开发 → `skill-creator` skill

---

#### 2. 组合使用形成工作流

- 📚 **学习工作流**: 阅读分析 → 笔记文档 → 知识分享
- 📊 **报告工作流**: 数据分析 → 可视化 → 演示汇报
- 🔧 **开发工作流**: MCP 开发 → Skill 创建 → Web 测试

---

#### 3. 参数明确清晰

提供清晰的需求描述:
- ✅ "使用 xlsx skill 创建销售报表,包含月度汇总和趋势图"
- ❌ "用 xlsx 做个表"

指定输出格式和要求:
- ✅ "生成 1080p PNG 和 PDF 格式"
- ❌ "生成图片"

---

#### 4. 利用批量能力

对于重复性任务,充分利用批量处理:
- 📄 批量 PDF 处理
- 📊 批量报表生成
- 🔍 批量内容分析

---

### ❌ 避免做法

#### 1. 不要误用 Skills

- ❌ 简单任务使用复杂 Skills
- ❌ 用通用方法代替专用 Skill
- ❌ 忽略 Skill 的限制和约束

#### 2. 不要忽略文件约束

注意:
- 文件大小限制 (如 Slack GIF 的 128KB)
- 格式兼容性
- 性能约束

#### 3. 不要跳过质量检查

- ❌ 不验证输出质量
- ❌ 不测试生成的代码
- ❌ 不审查生成的文档

---

## 常见问题

### Q1: 何时使用 pdf vs pdf-processing-pro?

**pdf**:
- ✅ 基本 PDF 操作
- ✅ 单个文件处理
- ✅ 表单填写和简单提取

**pdf-processing-pro**:
- ✅ 扫描件 OCR
- ✅ 批量处理大量文件
- ✅ 生产环境复杂工作流
- ✅ 需要高级验证和错误处理

---

### Q2: deep-reading-analyst 支持哪些思维框架?

支持 10+ 种思维框架:
- SCQA, 5W2H (快速分析)
- 批判性思维, 逆向思维
- 心智模型, 第一性原理
- 系统思维, 六顶思考帽
- SWOT, PEST

可根据问题复杂度选择不同组合。

---

### Q3: 如何创建自定义 Skill?

使用 `skill-creator` skill:

```python
# 1. 学习 Skill 开发
使用 skill-creator skill 学习如何创建 Skill

# 2. 初始化 Skill
运行: scripts/init_skill.py my-skill

# 3. 编辑 Skill
编辑 my-skill/skill.md

# 4. 打包 Skill
运行: scripts/package_skill.py my-skill
```

---

### Q4: 如何选择分析深度?

根据时间和需求选择:
- ⚡ **15 分钟** - 快速了解 → SCQA + 5W2H
- 📝 **30 分钟** - 标准分析 → + 批判性思维
- 🔬 **60 分钟** - 深度分析 → + 多种框架
- 📚 **120 分钟+** - 研究级分析 → + 跨来源对比

---

## 相关资源

- 📚 [Claude Code 官方文档](https://docs.claude.com/claude-code)
- 🎓 [MCP 协议文档](https://modelcontextprotocol.io/)
- 🔧 [Skill 开发指南](skill-creator/)
- 🎨 [p5.js 文档](https://p5js.org/)
- ⚛️ [React 文档](https://react.dev/)
- 🎨 [Tailwind CSS](https://tailwindcss.com/)
- 🧩 [shadcn/ui](https://ui.shadcn.com/)

---

**文档版本**: v2.0
**最后更新**: 2025-11-23
**Skills 总数**: 19
**维护者**: Claude Code Team

**Skills 目录位置**: `.claude/skills/`
**反馈与建议**: 如有问题或建议,请创建 GitHub Issue
