---
layout: post
title: "2 个 tool 覆盖 2500 个 endpoint——这是 Cloudflare MCP 的打法。"
date: 2026-04-23 12:16:00 +0800
source: https://claude.com/blog/building-agents-that-reach-production-systems-with-mcp
hero: /assets/mcp-production/2026-04-23_1000_mcp-production-hero-raw.png
topic_tags: [mcp, anthropic, claude-agents, production-infra, cloudflare, skills-plugin]
---

Anthropic 刚发的《Building agents that reach production systems with MCP》把 agent 连接生产系统的三层架构讲清楚了。图里五个数字,挑出来看:

• 300M / 月:MCP SDK 下载量,年初还是 100M,翻了 3 倍

• 85%+:加了 tool search 之后省下的工具定义 token

• 37%:复杂多步工作流用 code orchestration 省下的 token

• 1K tokens:Cloudflare 用 2 个工具穿透 2500 个 API endpoint,只吃这么多上下文

• 200+:官方目录里的 MCP server 数量

设计原则一句话——"fewer, well-described tools consistently outperform exhaustive API mirrors"。一个 create_issue_from_thread 胜过 get_thread + parse_messages + create_issue 三件套。

Skills 和 MCP 的分工也定了:MCP 给 agent 工具和数据的访问,Skills 教 agent 怎么用。Anthropic 自己的 data plugin 打包 10 skills + 8 MCP server(Snowflake / Databricks / BigQuery / Hex)作参照。

关注 @svtransit1 · 每天都有有用的 AI 资讯

https://claude.com/blog/building-agents-that-reach-production-systems-with-mcp

#AI #Claude #MCP #ClaudeCode
