---
layout: post
title: "GitHub 上还有一个仓库这周冲得猛——Lum1104/Understand-Anything,27.8K stars、2.4K forks、v2.7.3 是 5 月 19 号发的。"
date: 2026-05-25 15:10:57 +0800
source: https://github.com/Lum1104/Understand-Anything
hero: /assets/understand-anything-codebase-knowledge-graph/2026-05-25_1500_understand-anything-codebase-knowledge-graph-hero.png
topic_tags: [understand-anything, claude-code, cursor, copilot, gemini-cli, codebase-graph, cross-editor]
---

它做的事是「把任意 codebase 变成一张可交互的知识图」。文件、函数、类、依赖关系都是图里的节点。LLM 帮你拆,你拿浏览器逛。

值得放下来想的是它的接入方式——同一张图,Claude Code、Cursor、VS Code + Copilot、Copilot CLI、Gemini CLI 都能直接读。装的命令在 Claude Code 里就一行:`/plugin marketplace add Lum1104/Understand-Anything` 然后 `/plugin install understand-anything`。其他 IDE 走 `curl install.sh`。

这周早上我们贴过两条相邻的故事:Anthropic 自己挂出官方 plugin 目录、Imbad0202 那套学术研究流水线 skill 包。Understand-Anything 是这条线的下一层——前两个动作做的是「skill/工具层」的统一,这个仓库做的是「数据层」的统一。你的代码图,所有 agent 都能看见同一份,不再每个 IDE 各重建一遍。

更大的信号:codebase navigation 正在成为 agent 的第一类原语。过去你跟 LLM「聊代码」,它只能盯当前文件 + grep;再往下走必然是「指着一张图聊」——LLM 看图,你也看图,你们看的是同一张。

代码主页 + 在线 demo(understand-anything.com/demo/)放在第一条评论。在做大代码库 navigation 的朋友,值得试一遍。

转给那个还在让 Claude 「逐文件 read」的同事——graph 这个抽象,可能是接下来一年最被低估的代码 agent primitive。

主页 · 👇 第一条评论

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #DevTools #CodeGraph
