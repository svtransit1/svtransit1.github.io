---
layout: post
title: "你的 Claude Code 跑大仓库的 token 账单, 上周大概在心里痛过一次吗? 昨天上 GitHub trending 的 CodeGraph, 给了一个有数字的答案: 7 个真实 OSS 仓库各跑 4 轮, 中位 35% 成本下来, 71% tool call 干掉。🧱⚡"
date: 2026-05-28 12:00:00 +0800
hero: /assets/codegraph-coding-agent-token-graph/2026-05-28_0900_codegraph-coding-agent-token-graph-hero-1.png
---

作者 Colby McHenry, MIT license, 仓库才发布一天 star 已经冲到 2.98 万。它做的事很直接: 用 tree-sitter 把代码结构解析出来, 配上一层 LLM 语义索引, 落到本地 SQLite 数据库。

agent 想知道 「VS Code 的 command palette 怎么注册命令」, 一个 query 就能拿回完整调用链 — 不用 grep 一轮、read 三四个文件、再追类型那套来回探路。

整体中位 35% 成本 / 57% token / 46% 时间 / 71% tool call 全部往下走。最猛的几个: Excalidraw (640 个 TS 文件) 90% token + 96% tool call 干掉。Tokio (790 个 Rust 文件) 86% / 92%。VS Code 那个 1 万个 TS 文件的大块头, 也压到 78% / 85%。

效果较弱的也有: OkHttp (645 个 Java 文件) 只 13% / 45%, Django (3k Python) 36% / 53%。规律看起来挺清楚: 仓库越大、依赖越显式 (TS 的 import 树、Rust 的 mod 系统), 节省幅度越夸张; 全栈框架的动态注册 (Django / Rails 那种 runtime 绑定) 留给静态索引的余地就小。

技术细节: 20 种语言全覆盖, 14 个 web 框架做了 framework-aware 路由 (Django / Rails / Spring / Gin / Axum / NestJS 都识别)。一行 npx @colbymchenry/codegraph 装好, auto-sync file watcher 跟着代码改动同步, 全程 100% 本地, 不上传任何源码。

README 的 caveats 也写得诚实: WSL 的 /mnt 路径 SQLite WAL 模式会冲突, 大于 1MB 的文件直接跳过, Objective-C .mm 解析只做了一半。这种「这一块我没做完」的坦白, 比那些「全语言全场景全适配」的 README 可信多了。

agent context 这条赛道, 过去半年大部分人都在堆 RAG / 向量库 / 长 context 窗。CodeGraph 走的 graph-based 预索引这条路被低估了 — 把 agent 的输入从代码片段升级成代码结构, 比纯 retrieval 准得多, 也合理得多。仓库越大, 这个差距越夸张。

如果你的日常是 Claude Code / Cursor + 大仓库, 这周值得 npm 装一下试。

转给那个还在抱怨 token 账单的同事 👇

关注 @svtransit1 · 写给真在用 AI 的人

🧱 CodeGraph GitHub repo + 完整 7 仓库 benchmark 表 · 评论区取 ↓

#ClaudeCode #AIagent #AI工具 #开源 #GitHubTrending
