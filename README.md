# Qiqianqian / 齐浅浅

> 一个会随着对话逐步成长的 AI 陪伴应用静态站点。
> A static AI companion web app that grows with your conversations.

---

## 中文版

### 1. 项目简介

**Qiqianqian（齐浅浅）** 是一个以“陪伴式对话 + 本地记忆成长”为核心体验的前端应用。
从当前仓库内容来看，它已经被构建为可直接部署的静态网站：页面入口为 `index.html`，核心逻辑与样式位于 `assets/` 目录中，因此你可以把它理解为一个“开箱即可部署”的 Web 前端成品。

这个项目的核心体验包括：

- 与齐浅浅进行一对一聊天；
- 随对话生成新的“人格分面 / 联系人 / 群聊”；
- 在浏览器本地保存世界状态、消息、记忆与设置；
- 支持中英文界面切换；
- 支持导出 / 导入快照，方便迁移个人世界；
- 支持接入 OpenRouter / OpenAI 兼容接口，也支持无 Key 的本地 mock 浏览模式。

它更像是一个“可成长的 AI 陪伴宇宙”，而不是单纯的聊天窗口。

---

### 2. 功能概览

#### 2.1 陪伴式聊天

应用默认围绕“齐浅浅”展开，你可以直接与她聊天。界面中包含：

- 会话列表；
- 主聊天区；
- 侧边信息面板；
- Memory / Settings 等视图切换；
- 输入框、状态提示、打字反馈等基础聊天能力。

#### 2.2 QSeed 初始设定

首次进入时，应用会引导你填写一组初始化信息，用来建立你的个人世界种子（QSeed），例如：

- 你希望被如何称呼；
- 这个世界的名字；
- 偏好的陪伴语气；
- 你需要的支持；
- 你的边界。

这些信息会影响后续记忆生成、角色成长与互动风格。

#### 2.3 记忆系统

项目内置“Memory / Memories”相关能力，会根据互动内容沉淀记忆卡片，例如：

- 偏好；
- 情绪线索；
- 目标；
- 关系描述；
- 仪式感或长期主题。

这些记忆会被用于后续响应生成，使齐浅浅的陪伴更连续、更贴近你的上下文。

#### 2.4 成长型联系人与群组

除了主角色，应用还支持：

- 派生新的 facet（分面角色 / 联系人）；
- 自动形成 group（群组对话）；
- 在不同联系人之间组织不同风格的互动。

这意味着项目的设计目标并不是固定单角色，而是“从一个角色长出一个完整陪伴网络”。

#### 2.5 本地快照与迁移

项目支持：

- 导出 JSON 快照；
- 导入 JSON 快照；
- 重置本地世界。

如果你更换设备，或想备份长期积累的世界状态，这一能力非常重要。

#### 2.6 API Key 与模型配置

设置页提供了较完整的模型接入能力，支持：

- 配置 API Key；
- 选择 Key 存储模式；
- 获取模型列表；
- 解锁已保存 Key；
- 清除会话 Key；
- 在无 Key 时启用本地 mock 模式体验 UI。

同时还可以看到该项目兼容 **OpenRouter / OpenAI-compatible** 风格接口，适合接入多种大模型提供方。

---

### 3. 教程：如何使用

#### 3.1 直接本地打开

由于仓库已经包含构建产物，最简单的方式是直接使用静态服务器运行：

```bash
python3 -m http.server 8000
```

然后打开浏览器访问：

```text
http://localhost:8000
```

如果只是快速查看页面，也可以直接双击 `index.html`，但更推荐使用本地 HTTP 服务，以避免某些浏览器对模块脚本或资源路径的限制。

#### 3.2 首次进入

首次进入后，建议按以下步骤完成初始化：

1. 填写你的称呼；
2. 给你的世界命名；
3. 选择陪伴语气（如温柔、理性、轻松等）；
4. 写下你期待的支持；
5. 写下你的边界；
6. 进入主界面开始聊天。

#### 3.3 配置模型 API

如果你希望接入真实模型：

1. 进入 **Settings**；
2. 填入你的 API Key；
3. 选择存储方式；
4. 点击获取模型列表；
5. 保存设置；
6. 返回聊天页测试对话。

如果你暂时没有 API Key，也可以先启用 mock 模式浏览和体验交互流程。

#### 3.4 让齐浅浅“成长”

要让项目的特色真正体现出来，建议你：

- 持续进行多轮对话；
- 明确表达你的偏好、目标与情绪；
- 定期查看 Memory 面板；
- 尝试触发新的联系人或群聊；
- 定期导出 JSON 快照备份。

#### 3.5 数据备份建议

建议你在以下场景导出快照：

- 完成初始世界设定后；
- 聊天积累较多记忆后；
- 调整了关键配置后；
- 更换浏览器或设备前。

---

### 4. 技术信息

### 4.1 当前仓库结构

当前仓库比较精简，主要包括：

- `index.html`：站点入口；
- `assets/index-*.js`：前端逻辑打包产物；
- `assets/index-*.css`：样式打包产物；
- `favicon.svg`：站点图标；
- `CNAME`：自定义域名部署配置；
- `README.md`：项目说明。

这说明当前仓库更像是**前端构建后的发布目录**，而不是包含源码（如 `src/`、`package.json`）的开发仓库。

#### 4.2 技术栈推断

从构建产物可以推断本项目大概率使用了以下技术：

- **React**：JS 打包结果中可见 React 运行时代码；
- **现代模块化前端构建工具**：从资源命名方式推测，类似 Vite 一类的构建输出；
- **原生浏览器存储**：用于保存设置、世界快照、记忆和本地状态；
- **Web Crypto API**：用于本地加密 API Key；
- **Fetch API**：用于调用模型接口与获取模型列表。

#### 4.3 部署方式

这是典型的静态站点，可部署到：

- GitHub Pages；
- Cloudflare Pages；
- Netlify；
- Vercel（静态站点模式）；
- 任意 Nginx / Apache 静态服务器。

如果你已经绑定自定义域名，仓库中的 `CNAME` 文件可直接用于 GitHub Pages 一类的平台。

#### 4.4 数据与安全

项目明显强调“本地保存”能力，因此有几个特点值得注意：

- 你的世界状态主要保存在浏览器本地；
- API Key 可选择不同保存模式；
- 某些模式下支持本地加密；
- 导出快照时应注意妥善保管 JSON 文件；
- 若在公共设备使用，建议清除本地数据和会话 Key。

---

### 5. 适合谁使用

这个项目适合：

- 想做 AI 陪伴产品原型的人；
- 想研究“记忆 + 多角色成长”交互设计的人；
- 想部署一个静态前端 AI 应用的人；
- 想保存个人对话世界观和长期陪伴体验的人。

---

### 6. 未来可扩展方向

如果后续要继续迭代，比较值得补充的内容包括：

- 补充源码仓库或 `src/` 目录；
- 增加开发模式说明；
- 增加环境变量说明；
- 增加模型提供商适配说明；
- 增加数据结构与快照格式文档；
- 增加自动化测试与版本说明；
- 增加移动端适配与 PWA 说明。

---

## English Version

### 1. Overview

**Qiqianqian** is an AI companion web app centered on **relationship-style chatting + locally persisted memory growth**.
Based on the repository contents, this project is currently stored as a **deploy-ready static website**: `index.html` is the entry point, while the application logic and styles live in the `assets/` directory.

Core product ideas include:

- one-on-one chatting with Qiqianqian;
- growing new facets, contacts, and group conversations from ongoing dialogue;
- storing the world state, memories, conversations, and settings in the browser;
- switching between Chinese and English UI;
- exporting and importing snapshots for migration;
- connecting to OpenRouter / OpenAI-compatible APIs, with a local mock mode for UI exploration.

In short, this is closer to a **growing companion universe** than a simple chatbot window.

---

### 2. Feature Highlights

#### 2.1 Companion chat

The app is centered around chatting with Qiqianqian. The interface includes:

- a conversation list;
- a main chat area;
- an inspector / side panel;
- Memory and Settings views;
- text input, status banners, and typing feedback.

#### 2.2 QSeed onboarding

On first launch, the app asks the user to define an initial **QSeed**, such as:

- what Qiqianqian should call you;
- the name of your world;
- preferred companionship tone;
- what kind of support you want;
- your boundaries.

These signals shape future memory creation, interaction style, and character growth.

#### 2.3 Memory system

The app includes a memory layer that can retain information such as:

- preferences;
- emotional cues;
- goals;
- relationship context;
- recurring rituals or long-term themes.

This helps later responses feel more continuous and personalized.

#### 2.4 Growing contacts and groups

Beyond the main companion, the app also supports:

- generating new facets / derived contacts;
- creating group conversations;
- enabling different interaction styles across contacts.

That means the product is designed to evolve from one companion into a broader relationship network.

#### 2.5 Snapshot export and import

The app supports:

- exporting JSON snapshots;
- importing JSON snapshots;
- resetting the local world.

This is important for backup, portability, and long-term continuity.

#### 2.6 API and model settings

The Settings view appears to support:

- API key configuration;
- multiple key storage modes;
- model list fetching;
- unlocking stored keys;
- clearing runtime keys;
- enabling local mock mode when no key is available.

It is also clearly built to work with **OpenRouter / OpenAI-compatible** APIs.

---

### 3. Tutorial: How to Use

#### 3.1 Run locally

Because the repository already contains built assets, the easiest way to run it locally is with a static server:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

Opening `index.html` directly may work for quick inspection, but serving it over HTTP is recommended to avoid browser restrictions around module loading and asset paths.

#### 3.2 First-time setup

A recommended onboarding flow is:

1. enter your preferred name;
2. name your world;
3. choose a companionship tone;
4. describe the support you want;
5. define your boundaries;
6. enter the app and start chatting.

#### 3.3 Configure a model API

To connect a real model backend:

1. go to **Settings**;
2. enter your API key;
3. choose a storage mode;
4. fetch the available models;
5. save the configuration;
6. return to chat and test the conversation flow.

If you do not yet have an API key, you can still explore the UI by enabling local mock mode.

#### 3.4 Help Qiqianqian grow

To get the most out of the app, try to:

- keep chatting over multiple sessions;
- state your preferences, goals, and emotions clearly;
- review the Memory view from time to time;
- trigger new contacts or group conversations;
- export snapshots regularly.

#### 3.5 Backup suggestions

It is a good idea to export a snapshot when:

- you finish your initial setup;
- you have accumulated meaningful memories;
- you changed important settings;
- you are switching browsers or devices.

---

### 4. Technical Notes

#### 4.1 Repository structure

The current repository is minimal and mainly contains:

- `index.html`: site entry point;
- `assets/index-*.js`: bundled application logic;
- `assets/index-*.css`: bundled styles;
- `favicon.svg`: site icon;
- `CNAME`: custom domain deployment file;
- `README.md`: project documentation.

This strongly suggests that the repo is a **published frontend build output**, not the original source repository.

#### 4.2 Inferred tech stack

From the build artifacts, the app appears to use or rely on:

- **React**;
- a **modern frontend bundler** (likely something Vite-like based on asset naming patterns);
- **browser local storage** for local persistence;
- **Web Crypto API** for local API key encryption;
- **Fetch API** for model calls and model listing.

#### 4.3 Deployment

This project is a classic static web app and can be deployed to:

- GitHub Pages;
- Cloudflare Pages;
- Netlify;
- Vercel (static hosting);
- any Nginx or Apache static server.

The included `CNAME` file is useful for custom-domain hosting on platforms such as GitHub Pages.

#### 4.4 Data and safety

Because the app emphasizes local persistence, keep the following in mind:

- the world state is primarily stored in the browser;
- API keys may have multiple storage modes;
- some storage modes appear to support local encryption;
- exported JSON snapshots should be handled carefully;
- on shared devices, clearing local data and runtime keys is recommended.

---

### 5. Who This Is For

This project is a good fit for:

- builders prototyping AI companion products;
- designers exploring memory-driven, multi-character interaction systems;
- developers deploying static AI frontend experiences;
- users who want a portable, persistent personal companion world.

---

### 6. Suggested Next Steps

Good future improvements could include:

- adding the original source code or a `src/` directory;
- documenting local development steps;
- documenting environment variables;
- documenting provider integrations;
- documenting snapshot schema and data structures;
- adding automated tests and release notes;
- improving mobile/PWA documentation.

---

## License / 许可

当前仓库中未看到明确的开源许可证文件。
如需开源分发，建议补充 `LICENSE`。

No explicit open-source license file is currently present in the repository.
If you plan to distribute this project, consider adding a `LICENSE` file.
