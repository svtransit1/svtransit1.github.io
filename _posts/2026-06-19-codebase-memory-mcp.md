---
layout: post
title: "你的 coding agent 每次找段代码,都得把大半个 repo 翻一遍——token 就这么哗哗烧掉了 🧐。"
date: 2026-06-19 12:13:15 +0800
source: https://github.com/DeusData/codebase-memory-mcp
hero: /assets/codebase-memory-mcp/2026-06-19_1200_codebase-memory-mcp-hero.png
topic_tags: [codebase-memory, mcp, claude-code, token-cost, knowledge-graph]
---

有个挺火的开源工具想治这个:codebase-memory-mcp(7000 多 star)。它先把整个代码库索引成一张"知识图谱",agent 要查结构,直接查图,不用再一个文件一个文件地 grep。

官方给的对比挺唬人 🤔:同样五个结构查询,grep 全库要烧 41 万 token,查图只要 3400——等于砍掉 99%。索引也快,整个 Linux 内核、2800 万行代码,三分钟建完。

但这个"99%"你得看清是跟谁比——是跟"最笨的 grep 全库"比的 ⚠️。真正值钱的其实不是这个百分比,是那张图本身:agent 不用再漫无目的地翻文件了。

说到底,agentic coding 现在拼的早就不只是谁更聪明,是谁读得更省。把代码库变成一张能直接查的图,agent 不用乱翻,token 不用乱烧——这才是它真正卖的东西。

你会给自己的 Claude Code 接一个这种"代码库记忆"吗?

项目地址 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #MCP #开源
