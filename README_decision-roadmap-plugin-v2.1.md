# Decision Roadmap — AI Conversation Tracker

> **🌐 Language / 语言**
> - [English Documentation](#english-documentation) — see below
> - [中文文档](#中文文档) — 请往下滚动

Created by **AmytheCh**

---

<a id="english-documentation"></a>

# English Documentation

**Turn messy AI conversations into structured decision trees.**

## What is this?

Decision Roadmap is a Chrome browser extension that adds a persistent sidebar to your AI chat interface. It scans your conversation and organizes it into a structured decision tree — so you always know what's been discussed, what's been decided, and what's still open.

### Key Features

- **One-click analysis** — Click "Analyze Conversation" and get an instant structured overview. No API key needed, no extra cost. Everything runs locally in your browser.
- **6-dimension information model** — Each topic node captures: Problem, Discussion, Decision, Basis, Risks/Trade-offs, and Action Items.
- **4 status states** — Decided (green), Discussing (amber), Pending (gray), Blocked (red). Filter by any status with one click.
- **Jump to source** — Click "Jump to source" on any node to scroll back to the exact message in the conversation, highlighted with a green flash.
- **Bilingual UI** — Toggle between English and Chinese with one click.
- **Persistent data** — Your decision tree is saved locally. It survives page refreshes.
- **Privacy first** — Zero data leaves your browser. No external requests. No tracking.

---

## Supported Platforms

| Platform | Status | Notes |
|----------|--------|-------|
| **Claude** (claude.ai) | ✅ Fully supported | Tested and optimized |
| **ChatGPT** (chatgpt.com) | ⚠️ Beta | Basic support, may need selector updates |
| **Gemini** (gemini.google.com) | ⚠️ Limited | Lazy-loading limits extraction to visible messages |

> **Note**: This extension works in Chrome and all Chromium-based browsers (Edge, Arc, Brave, Opera). Firefox and Safari are not supported yet.

---

## Installation

### Step 1: Download

Download the latest release ZIP from the [Releases](../../releases) page, or clone this repository:

```bash
git clone https://github.com/YOUR_USERNAME/decision-roadmap.git
```

### Step 2: Load the extension

1. Open Chrome and navigate to `chrome://extensions/`
2. Enable **Developer mode** (toggle in the top-right corner)
3. Click **Load unpacked**
4. Select the `plugin` folder from the downloaded/cloned files
5. The extension icon will appear in your browser toolbar

### Step 3: Pin it (recommended)

Click the puzzle icon (🧩) in the toolbar → find "Decision Roadmap" → click the pin icon to keep it visible.

---

## How to Use

### Open the sidebar

Two ways:
- Click the **home-button style icon** in the bottom-right corner of the page
- Press **`Cmd+Shift+D`** (Mac) or **`Ctrl+Shift+D`** (Windows/Linux)

### Analyze a conversation

1. Open any conversation on a supported platform (e.g., claude.ai)
2. Open the sidebar
3. Click **"▶ Analyze Conversation"**
4. The decision tree appears instantly in the sidebar

### Browse and filter

- **Click any node** to expand and see the 6-dimension breakdown
- **Use filter chips** (All / Decided / Discussing / Pending / Blocked) to focus on specific statuses
- **Click "Jump to source"** to scroll back to the original message

### Switch language

Click the **"中文"** or **"EN"** button in the sidebar header.

---

## Status Guide

| Color | Status | Meaning |
|-------|--------|---------|
| 🟢 Green | **Decided** | A conclusion has been reached |
| 🟡 Amber | **Discussing** | Under active discussion |
| ⚪ Gray | **Pending** | Mentioned but not yet started |
| 🔴 Red | **Blocked** | Waiting on a dependency |

---

## The 6 Dimensions

| Dimension | What it captures |
|-----------|-----------------|
| **Problem** | The specific question or pain point being discussed |
| **Discussion** | Summary of the key arguments and comparisons |
| **Decision** | The conclusion reached (if any) |
| **Basis** | Why this option was chosen |
| **Risks / Trade-offs** | What risks were accepted or options rejected |
| **Action Items** | Next steps with completion status |

---

## How It Works

The extension uses **local keyword-based analysis** — no AI API calls, no token consumption.

1. It reads conversation messages directly from the page DOM
2. Groups messages into conversation turns (user question + AI response)
3. Scans for decision-related keywords to classify each turn
4. Renders the structured tree in the sidebar

This means analysis is **instant** and **free**, but may be less precise than AI-powered analysis for complex discussions.

---

## File Structure

```
plugin/
├── manifest.json          # Chrome extension manifest (V3)
├── css/
│   └── sidebar.css        # Sidebar styling (light & dark mode)
├── js/
│   ├── background.js      # Service worker (icon click handler)
│   ├── extractor.js       # DOM scraping (per-platform selectors)
│   ├── local-analyzer.js  # Keyword-based local analysis engine
│   ├── sidebar.js         # Sidebar UI rendering & state management
│   └── main.js            # Entry point & event binding
└── icons/
    ├── icon48.png
    └── icon128.png
```

---

## FAQ

**Q: Does it work on the Claude desktop app?**
A: No. The desktop app doesn't support Chrome extensions. Use claude.ai in your browser instead — the functionality is identical.

**Q: Is my data sent anywhere?**
A: No. All processing happens locally. No data leaves your browser, ever.

**Q: Why is the analysis not very accurate?**
A: The current version uses keyword matching, not AI. It's best at identifying the structure of your conversation (what topics were discussed, in what order) rather than deeply understanding the content. AI-powered analysis is planned for a future version.

**Q: Can I use this on Firefox or Safari?**
A: Not yet. The current version supports Chromium-based browsers only. Other browser support is planned.

---

## Roadmap

- [x] V1 — Sidebar UI, DOM extraction, status filtering, scroll-to-source
- [x] V2.1 — Local keyword analysis, bilingual UI, Claude & Gemini support
- [ ] V3 — AI-powered analysis (optional, with API key)
- [ ] V3 — Additional platform support (Doubao, Yuanbao, Qianwen)
- [ ] V3 — Mermaid.js visual tree rendering
- [ ] V3 — Export to Markdown / JSON

---

## License

All rights reserved. Created by **AmytheCh**.

## Acknowledgements

Built with the assistance of Claude (Anthropic).

---

<a id="中文文档"></a>

# 中文文档

**将杂乱的 AI 对话整理为结构化的决策树。**

## 这是什么？

Decision Roadmap 是一个 Chrome 浏览器扩展，在你的 AI 聊天界面旁边添加一个常驻侧边栏。它扫描你的对话内容，将其整理为结构化的决策树——让你随时掌握讨论了什么、决定了什么、还有什么悬而未决。

### 核心功能

- **一键分析** — 点击"分析对话"即刻生成结构化概览。无需 API Key，无额外费用。所有处理在浏览器本地完成。
- **六维信息模型** — 每个议题节点包含：问题定义、讨论过程、决策结论、决策依据、风险与取舍、待办事项。
- **四种状态标记** — 已决策（绿）、讨论中（黄）、待启动（灰）、阻塞（红）。一键筛选任意状态。
- **跳转到原文** — 点击任意节点的"跳转到原文"，对话页面自动滚动到对应消息并绿色高亮闪烁。
- **中英双语** — 一键切换中文和英文界面。
- **数据持久化** — 决策树保存在本地，刷新页面不丢失。
- **隐私优先** — 数据不离开你的浏览器。无外部请求，无追踪。

---

## 支持平台

| 平台 | 状态 | 备注 |
|------|------|------|
| **Claude** (claude.ai) | ✅ 完全支持 | 已测试并优化 |
| **ChatGPT** (chatgpt.com) | ⚠️ 测试中 | 基础支持，选择器可能需要更新 |
| **Gemini** (gemini.google.com) | ⚠️ 有限支持 | 懒加载机制限制了可提取的消息范围 |

> **注意**：本扩展适用于 Chrome 及所有基于 Chromium 的浏览器（Edge、Arc、Brave、Opera）。暂不支持 Firefox 和 Safari。

---

## 安装步骤

### 第一步：下载

从 [Releases](../../releases) 页面下载最新版本的 ZIP 文件，或者克隆本仓库：

```bash
git clone https://github.com/YOUR_USERNAME/decision-roadmap.git
```

### 第二步：加载扩展

1. 打开 Chrome，地址栏输入 `chrome://extensions/`
2. 开启右上角的 **开发者模式**
3. 点击 **加载已解压的扩展程序**
4. 选择下载/克隆的 `plugin` 文件夹
5. 扩展图标将出现在浏览器工具栏中

### 第三步：固定到工具栏（推荐）

点击工具栏的拼图图标（🧩）→ 找到"Decision Roadmap"→ 点击图钉固定。

---

## 使用方法

### 打开侧边栏

两种方式：
- 点击页面右下角的 **方形小按钮**
- 按 **`Cmd+Shift+D`**（Mac）或 **`Ctrl+Shift+D`**（Windows/Linux）

### 分析对话

1. 在支持的平台上打开任意对话（如 claude.ai）
2. 打开侧边栏
3. 点击 **"▶ 分析对话"**
4. 决策树立即出现在侧边栏中

### 浏览与筛选

- **点击任意节点** 展开查看六维详细信息
- **使用筛选按钮**（全部 / 已决策 / 讨论中 / 待启动 / 阻塞）聚焦特定状态
- **点击"跳转到原文"** 滚动回对应的原始消息

### 切换语言

点击侧边栏顶部的 **"中文"** 或 **"EN"** 按钮。

---

## 状态说明

| 颜色 | 状态 | 含义 |
|------|------|------|
| 🟢 绿色 | **已决策** | 已得出结论 |
| 🟡 黄色 | **讨论中** | 正在讨论 |
| ⚪ 灰色 | **待启动** | 已提及但尚未开始 |
| 🔴 红色 | **阻塞** | 等待前置条件 |

---

## 六维信息模型

| 维度 | 捕获内容 |
|------|----------|
| **问题定义** | 正在讨论的具体问题或痛点 |
| **讨论过程** | 核心论点和方案对比的摘要 |
| **决策结论** | 得出的结论（如有） |
| **决策依据** | 选择该方案的核心理由 |
| **风险与取舍** | 被接受的风险或被否决的方案 |
| **待办事项** | 下一步行动及完成状态 |

---

## 工作原理

本扩展使用 **本地关键词分析** — 不调用 AI API，不消耗 Token。

1. 直接从页面 DOM 读取对话消息
2. 将消息按轮次分组（用户提问 + AI 回复）
3. 通过关键词扫描对每轮进行分类
4. 在侧边栏中渲染结构化决策树

因此分析 **瞬间完成** 且 **完全免费**，但对复杂讨论的分析精度可能不如 AI 驱动的方案。

---

## 文件结构

```
plugin/
├── manifest.json          # Chrome 扩展清单文件 (V3)
├── css/
│   └── sidebar.css        # 侧边栏样式（支持浅色/深色模式）
├── js/
│   ├── background.js      # Service Worker（图标点击处理）
│   ├── extractor.js       # DOM 抓取（各平台选择器）
│   ├── local-analyzer.js  # 基于关键词的本地分析引擎
│   ├── sidebar.js         # 侧边栏 UI 渲染与状态管理
│   └── main.js            # 入口文件与事件绑定
└── icons/
    ├── icon48.png
    └── icon128.png
```

---

## 常见问题

**Q: 桌面端 App 能用吗？**
A: 不能。桌面端不支持 Chrome 扩展。请用浏览器访问 claude.ai，功能完全一样。

**Q: 我的数据会被发送到外部吗？**
A: 不会。所有处理在本地完成，数据永远不会离开你的浏览器。

**Q: 为什么分析结果不够准确？**
A: 当前版本使用关键词匹配而非 AI 分析。它更擅长识别对话结构（讨论了哪些话题、顺序如何），而非深度理解内容。AI 驱动的分析将在未来版本中推出。

**Q: 支持 Firefox 或 Safari 吗？**
A: 暂时不支持。当前版本仅支持 Chromium 系浏览器，其他浏览器的适配已在计划中。

---

## 开发路线

- [x] V1 — 侧边栏 UI、DOM 提取、状态筛选、跳转到原文
- [x] V2.1 — 本地关键词分析、中英双语 UI、Claude 与 Gemini 支持
- [ ] V3 — AI 驱动的分析（可选，需 API Key）
- [ ] V3 — 更多平台支持（豆包、元宝、千问）
- [ ] V3 — Mermaid.js 可视化决策树渲染
- [ ] V3 — 导出为 Markdown / JSON

---

## 许可

保留所有权利。由 **AmytheCh** 创建。

## 致谢

借助 Claude（Anthropic）协助开发。

---

<p align="center"><strong>Created by AmytheCh</strong></p>
