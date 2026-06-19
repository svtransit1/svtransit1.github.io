---
layout: post
title: "\"我接一个 MCP server 就得授权一遍,接十个授权十遍——这破事就不能一次搞定?\" 🧐 如果你用 Claude Code 接过一堆工具,这句话你大概率说过。"
date: 2026-06-19 09:12:57 +0800
source: https://blog.modelcontextprotocol.io/posts/enterprise-managed-auth/
hero: /assets/mcp-enterprise-auth/2026-06-19_0900_mcp-enterprise-auth-hero.png
topic_tags: [mcp, oauth, claude-code, enterprise, ai-agent]
---

这周 MCP 官方真把它办了:上线了一个叫 Enterprise-Managed Authorization(企业托管授权,简称 EMA)的扩展,而且已经标成"稳定"了。

先说它把流程怎么反过来的。以前你每接一个 server——Figma、Linear、Asana——都得单独走一遍 OAuth,弹个框问你"是否授权",你点一次同意;十个工具就是十遍。EMA 之后:你公司在身份系统里(比如 Okta)把策略配好,你第一次登录,该连的 server 自动全给你连上,中间一个授权框都不弹。技术上是用一个叫 ID-JAG 的令牌,在单点登录的时候顺手换好。

已经接上的:客户端有 Claude、Claude Code、Cowork、还有 VS Code;server 那边 Figma、Linear、Asana、Atlassian、Canva、Supabase 都在列,Slack 也在加 💪。

但这里有个你得想清楚的交易 ⚠️:方便是真方便,可"决定你能连哪些 server"这个权力,从你手里,挪到了 IT 手里。对公司是好事——能统一管、能留审计、工作号和私人号不再混着。对你个人,意味着以后你能用哪些 AI 工具,是管理员说了算,不全是你说了算。

所以这事不只是"少点几次同意"。它是 MCP 从"开发者各玩各的",往"企业统一管控"走的一步。说到底,你能接哪些 AI 工具,以后不用你操心了——但也由不得你了。

你愿意为"一次登录全连上",让公司替你决定能接哪些 AI 工具吗?

原文 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #MCP #ClaudeCode #AIagent
