---
layout: post
title: "每次重开 Claude Code，上下文就清零了——这事儿有插件能治。"
date: 2026-04-21 21:08:13 +0800
source: https://github.com/thedotmack/claude-mem
hero: /assets/claude-mem/2026-04-21_2105_claude-mem-hero.png
topic_tags: [claude-code, memory, plugin, open-source]
---

叫 claude-mem，这周在 GitHub 冲到 6.4 万星。作者 Alex Newman 想解决的是每个 Claude Code 用户都撞过的场景：新会话打开，AI 完全不记得上次聊了什么，你得把项目背景重新喂一遍，token 哗哗烧。

他的做法是让 Claude 自己挂钩子。插件注册了 SessionStart、UserPromptSubmit、PostToolUse 等 5 个生命周期节点，会话里每一步操作都顺手被抓下来。Bun 起了个 worker 服务跑在 37777 端口，顺便给一个本地 Web UI 让你能直接看记忆流。存储层用 SQLite 加 Chroma 向量库——关键词搜索和语义搜索混在一起。

取记忆的地方是最巧的一层。插件不会把所有历史一股脑塞回去，走的是 index → timeline → details 三层渐进式披露：先给 Claude 一个目录，需要哪块再拉哪块的详情。作者说这套下来，比盲喂整段历史能省大概 90% 的 token。

装法一行：

    npx claude-mem install

重启 Claude Code，插件自动激活。同时兼容 Gemini CLI 和 OpenCode。敏感内容用 `<private>` 标签包起来会被直接跳过。最近的 v12.3.8 加了简体中文模式（code--zh），对国内用户挺友好。

AGPL-3.0 开源，仓库：github.com/thedotmack/claude-mem

现在 AI 编程工具都在想办法解决「长上下文 + 会话连贯」。Anthropic 官方的 Skills 和 Plugin 市场是一条路，第三方工具像 claude-mem 是另一条。两条并行跑，看哪种能沉淀出真正顺手的工作流。

转给那个还在每次会话手动贴项目背景的朋友——他们会想装一下。

关注 @svtransit1 · 每天都有有用的 AI 资讯

#AI #ClaudeCode #AI工具 #开源
