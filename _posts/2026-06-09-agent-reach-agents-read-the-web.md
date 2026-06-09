---
layout: post
title: "你的 AI agent,现在能自己上微博、小红书、B站、推特、YouTube 翻资料了 🤯——还不用买任何 API。"
date: 2026-06-09 18:23:55 +0800
source: https://github.com/Panniantong/Agent-Reach
hero: /assets/agent-reach-agents-read-the-web/2026-06-09_1800_agent-reach-agents-read-the-web-hero.png
topic_tags: [agent-reach, ai-agent, web-access, mcp, claude-code, china-platforms]
---

有个开源工具叫 Agent-Reach(GitHub 已经 2.5 万星),干的就是这件事。一条命令 agent-reach install,它替你把一堆现成的命令行工具(twitter-cli、yt-dlp、小红书、B站那些)装好配好,再给你的 agent(Claude Code、Cursor 都行)塞一份 SKILL 说明书。之后 agent 要查料,直接调这些工具就行,你不用再为每个平台单独申请 key、配账号、绕反爬 🛠️。

它能读的清单是真的长:推特、Reddit、YouTube、GitHub、B站、小红书、抖音、领英、微信公众号、微博、V2EX、雪球、小宇宙,再加任意网页和 RSS。中文圈、英文圈的主要信息源,基本一网打尽。

一个让人安心的细节:cookie 只存在你本地(~/.agent-reach,权限 600),作者明说不上传、不外泄 🔒。

提醒一句 ⚠️:像推特、小红书这种要 cookie 登录的,脚本访问本身有封号风险——作者建议拿小号,别拿主号去试。

说到底,这东西戳中的是 agent 一个真痛点:模型再聪明,够不到新鲜的、墙内墙外的真实信息,也只能干瞪眼。给它一双能自己上网的手,有时候比换个更大的模型还顶用。

你会放心让你的 agent,自己去刷小红书帮你找资料吗?

转给那个天天喊「让 AI 帮我查一下」的朋友 👇

原始出处 · 第一条评论拿

关注 @svtransit1 · 写给真在用 AI 的人

#AI #AIagent #ClaudeCode #开源工具 #MCP
