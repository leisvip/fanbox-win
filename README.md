<div align="center">

# 📦 FanBox Windows

> *"AI spins up ten projects in an afternoon. FanBox helps you find them again."*

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Release](https://img.shields.io/badge/Release-1.8.0-blue)](https://github.com/leisvip/fanbox-win/releases/latest)
[![Platform](https://img.shields.io/badge/Platform-Windows-blueviolet?logo=windows)](https://github.com/leisvip/fanbox-win/releases/latest)
[![Based on](https://img.shields.io/badge/Based%20on-alchaincyf%2Ffanbox-orange)](https://github.com/alchaincyf/fanbox)

**The cockpit for vibe coding: browse files on the left, command agents on the right, watch every change in between.**

FanBox Windows 是基于 [花叔 Huashu](https://github.com/alchaincyf) 的 [alchaincyf/fanbox](https://github.com/alchaincyf/fanbox) 重构的 **Windows 版本**，保留原版核心功能，适配 Windows 平台特性。

[⬇ Download](https://github.com/leisvip/fanbox-win/releases/latest) · [Features](#features) · [Install](#install) · [Credits](#credits) · [Based on](#based-on)

</div>

---

## 为什么做 FanBox Windows

原版 [alchaincyf/fanbox](https://github.com/alchaincyf/fanbox) 是 macOS 专属的 Electron 应用，Windows 用户无法使用。本项目基于原版代码进行重构，主要改动包括：

- **平台适配**：将 macOS 专用的系统调用替换为 Windows 兼容方案
- **文件操作**：适配 Windows 文件路径和系统命令
- **打包构建**：支持 Windows NSIS 安装包构建
- **路径识别**：终端输出的 Windows 路径可正确识别和点击

> ⚠️ 本项目是原版的 Windows 移植版本，所有核心功能和设计均来自原版，仅做平台适配。

---

## Features

### Files · find & preview

- **⌘K global fuzzy search** — a fragment of the name is enough; `⌘↵` opens the project in your editor; `content:keyword` switches to full-text search.
- **Bold solid icons** — every file type "looks like itself": red PDFs, yellow JS, blue Markdown.
- **Preview in place** — rendered Markdown, live HTML, syntax-highlighted code, inline images/video/PDF.
- **Thumbnail speed** — scrolling and clicking through large folders stays under 0.1s.

### Watch what the agent changed

- **A live dashboard** — every file the agent writes makes its card ripple and glow by change frequency.
- **Follow mode** — one click and the file view + preview track whatever file the agent edits.
- **Session replay** — drag the timeline like scrubbing a video to replay which files the agent touched.
- **Change inbox** — all files modified this session, aggregated across projects.
- **Git diff** — Monaco read-only DiffEditor, HEAD vs working tree side by side.

### Agent cockpit

- **Project memory** — open any project folder and see what AI did there: past sessions, changed files, triggered skills — and a "resume" button.
- **Screenshot express** — take a system screenshot and a card pops up: feed it to the terminal agent, file it, or annotate before sending.
- **AI organize** — AI proposes a cleanup plan from metadata only; you approve each move; FanBox executes with a rollback log and one-click undo.
- **Release wizard** — version bump, CHANGELOG promotion, build, push and GitHub Release composed into one command sequence.
- **Skills X-ray** — every agent skill on your machine in one view.
- **Agent usage** — Claude Code official 5h window / weekly quota plus local token statistics.

### Terminal · command the agent

- **A real embedded terminal** — node-pty + xterm.js (WebGL). Claude Code / vim / htop render correctly.
- **Drag files in** — drop a file or folder into the terminal to insert its path as agent context.
- **Clickable paths** — file paths appearing in terminal output open in FanBox on click.
- **Send selection** — select text in a preview and fling it into the terminal with file provenance + fencing.

### Editing · WYSIWYG

- **Markdown** — Milkdown Crepe, Notion-style WYSIWYG.
- **Code/JSON** — Monaco (the VS Code core), themed per skin.
- **Image annotation** — pen/arrow/text/redaction, format conversion, compression, resizing.
- **Unsaved guard** — all three editors intercept unsaved exits.

---

## Install

### Windows Installer (Recommended)

Download the latest `.exe` installer from [**Releases**](https://github.com/leisvip/fanbox-win/releases/latest) and run it.

### Web (no packaging)

```bash
node server.js
```

Open `http://localhost:4567`. Zero dependencies, zero build — clone and run.

### Development

```bash
npm install
npm run app          # electron . — full desktop app
npm run dist:win     # build Windows installer
```

---

## Project Structure

```
fanbox-win/
├── server.js               # Zero-dependency Node backend (file APIs + thumbnails + static)
├── electron/
│   ├── main.js             # Main process (window/pty/clipboard/fs.watch/menu)
│   └── preload.js          # Exposes fanboxPty / fanboxFs / fanboxClipboard
├── public/
│   ├── index.html
│   ├── style.css
│   ├── app.js              # Frontend single-page app
│   └── vendor/             # xterm / monaco / milkdown local assets
├── src-vendor/             # esbuild entries producing public/vendor/milkdown
├── build/                  # Icons + entitlements
├── docs/                   # Concepts/PRD/roadmap/acceptance criteria
└── 素材/                   # Assets
```

---

## Tech Stack

| Layer | Stack |
|---|---|
| Backend | Zero-dependency Node.js `server.js` |
| Desktop shell | Electron 33 + node-pty |
| Terminal | xterm.js + WebGL + unicode11 |
| Editors | Monaco (code) + Milkdown Crepe (Markdown) |
| Packaging | electron-builder → Windows NSIS installer |

---

## Based on

本项目基于以下优秀开源项目重构：

| Project | Used for | License |
|---|---|---|
| [alchaincyf/fanbox](https://github.com/alchaincyf/fanbox) | 原版 macOS 实现，本项目的代码基础 | MIT |
| [Electron](https://www.electronjs.org/) | The desktop shell | MIT |
| [node-pty](https://github.com/microsoft/node-pty) | Pseudo-terminal for embedded shell | MIT |
| [xterm.js](https://xtermjs.org/) | Terminal rendering | MIT |
| [Monaco Editor](https://microsoft.github.io/monaco-editor/) | Code/JSON editing and Git diff view | MIT |
| [Milkdown](https://milkdown.dev/) (Crepe) | Markdown WYSIWYG editing | MIT |

---

## Credits

### Windows 版作者

**leisvip** — 基于原版进行 Windows 平台适配和重构。

| Platform | Link |
|------|------|
| 🌐 Web | [cozes.top](https://cozes.top/s) |
| 📺 Bilibili | [leisvip](https://space.bilibili.com/397302381) |
| 💻 GitHub | [leisvip](https://github.com/leisvip) |

### 原版作者

**花叔 Huashu** — AI Native Coder, indie developer. Known for Cat Light (App Store paid chart Top 1).

| Platform | Link |
|------|------|
| 🌐 Web | [bookai.top](https://bookai.top) · [huasheng.ai](https://www.huasheng.ai) |
| 𝕏 Twitter | [@AlchainHust](https://x.com/AlchainHust) |
| 📺 Bilibili | [花叔](https://space.bilibili.com/14097567) |
| 📕 Xiaohongshu | [花叔](https://www.xiaohongshu.com/user/profile/5abc6f17e8ac2b109179dfdf) |

---

## Acknowledgment

本项目完全基于 [alchaincyf/fanbox](https://github.com/alchaincyf/fanbox) 的代码重构而来，所有核心功能、设计理念、UI 设计均来自花叔的原作。在此对花叔的优秀开源项目表示感谢。

---

<div align="center">

**Finder** manages your files. **IDEs** write your code.<br>
**FanBox** shows you what AI did on your machine.<br><br>

MIT License © [花叔 Huashu](https://github.com/alchaincyf) (Original) · [leisvip](https://github.com/leisvip) (Windows Port)

</div>
