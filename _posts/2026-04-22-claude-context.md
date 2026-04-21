---
layout: post
title: "处理大 codebase 还在把整个目录贴进 Claude Code？这条路作者说能省 40% token——zilliztech 开源的 claude-context，今天 GitHub daily trending 第三。"
date: 2026-04-22 03:08:16 +0800
source: https://github.com/zilliztech/claude-context
hero: /assets/claude-context/2026-04-22_0015_claude-context-hero.png
topic_tags: [claude-code, mcp, vector-search, open-source]
---

思路是给 Claude / Cursor / Codex CLI 挂一个 MCP 插件，后面连 Milvus 或 Zilliz Cloud 做向量库。代码库提前索引一次，查询时走 BM25 + 密集向量的混合搜索，只把相关片段喂给模型——Claude 不用每次自己 grep 整个目录了。

摆在老办法旁边比较：

token 成本：直接贴代码 = 100%，走 claude-context ≈ 60%，作者说检索质量相当。

接入成本：一行 claude mcp add claude-context + Zilliz Cloud 账号（免费额度够用）+ OpenAI embedding key。装完对话里多四个工具（index_codebase、search_code、clear_index、get_indexing_status），一句「把这个项目索引一下」就行。

覆盖范围：Claude Code、Cursor、VS Code、Codex CLI、Gemini CLI、Cline 都能接。跟昨天聊的 claude-mem 是两个方向的补齐——一个管会话记忆，一个管代码库搜索。

什么时候值得装？项目够大、长上下文按 token 计费、或者想在多个编辑器共用同一套索引——这三种场景下能回本。小项目直接贴代码就够。

MIT，6.5K 星：github.com/zilliztech/claude-context

转给那个还在每次把整个目录塞进 Claude 的同事。

关注 @svtransit1 · 每天都有有用的 AI 资讯

#AI #ClaudeCode #MCP #AI工具
