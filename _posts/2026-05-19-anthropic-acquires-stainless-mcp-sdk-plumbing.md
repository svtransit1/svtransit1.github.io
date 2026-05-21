---
layout: post
title: "每个 Anthropic 官方 SDK,过去几年都是同一家公司生成的。"
date: 2026-05-19 12:00:00 +0800
source: https://www.anthropic.com/news/anthropic-acquires-stainless
hero: /assets/anthropic-acquires-stainless-mcp-sdk-plumbing/2026-05-19_0930_anthropic-acquires-stainless-mcp-sdk-plumbing-hero.png
topic_tags: [anthropic, stainless, mcp, sdk, agent-infrastructure, acquisition, openapi]
---

昨天(5 月 18 日),Anthropic 宣布把这家公司 —— Stainless —— 直接收了。

Stainless 干的事很具体:你给它一份 API spec,它给你 TypeScript / Python / Go / Java / Kotlin 的 SDK,还顺手出一份 CLI 和一个 MCP server。"几百家公司" 在用。客户名单他们没全公开,但他们自己说从 Anthropic API 最早期开始,所有官方 SDK 就是 Stainless 自动生成的。

也就是说,你 pip install anthropic 或者 npm i @anthropic-ai/sdk,跑出来的代码不是 Anthropic 工程师一行一行手敲的,是 Stainless 帮他们从 OpenAPI spec 一键编译出来的。这件事 Anthropic 公开承认,等于把"我们最 stable 的开发者接触面"外包给了一家初创。

现在他们把这家初创买了。

Stainless 创始人 Alex Rattray 在公告里说,"团队可以继续做我们热爱的事,在最重要的平台上做"。话说得漂亮,大白话是 —— 我们进 Anthropic 之后还是搞 SDK / CLI / MCP 这套,但只给 Claude 一家做。其他几百家客户怎么办?没说。金额?没披露。

Anthropic 给的官方理由是一句话:

"Agents are only as useful as what they can connect to."

翻成中文 —— agent 能用到什么程度,取决于它能连到多少东西。

这句话放在今天的时间点看,意思特别重。这个礼拜社区反复在讨论的几件事 —— Hermes Agent 把 Claude Pro / ChatGPT Pro 的 OAuth 拆成本地 API,agentmemory 把 LLM Wiki 做成 npm 装,Archestra 用 Git author / committer 字段干扰 AI agent 灌水 —— 全都是 agent 跟工具之间的"接合面"问题。Anthropic 这一手收购,等于把这件事的官方版正式收编进核心团队。

往回看一年,MCP 是 Anthropic 2024 年底放出的开源协议,生态里几百家公司、几万个 server 在写。最快速增长的工具链就是 Stainless 这种"从 spec 自动生成 server"的自动化层。Anthropic 自己写了协议、放给社区,然后买下了协议落地最关键的一家工具厂 —— 这是一个非常 Microsoft 式的动作。

看到这件事,我脑子里浮起两个想法。

一个,MCP 不再是开源生态的纯民间项目了。Anthropic 自己买下了 MCP server 自动生成的最强工具链,在协议层和工具层都拿到了一手控制权。对 MCP 这个标准本身可能是好事 —— 标准化加速,生态扩张 —— 但小工具厂商之后跟 Anthropic 之间的关系会更微妙。今天还在做 MCP 相关的初创,要想清楚自己是在"垫脚"还是在"被收编路径上"。

第二个,SDK 不再是"工程师的体力活"。手写 SDK 的项目这个赛道要重新算账了。一份 OpenAPI spec 进去,五种语言 SDK + CLI + MCP server 出来,Stainless 已经把这件事做成商品。如果你公司还在养一个专门的 SDK 维护团队,看看现在的人月成本和工具成本差距。这事在 Claude 之外也成立 —— 任何有公共 API 的公司,都该把 SDK 自动化纳入选项,不然下一波被竞争对手"接合面快"打到的就是你。

放大一点看,Anthropic 这一年的收购动作 —— 从开发者工具到 SDK 自动化 —— 是把开发体验链条上一段段拼回来。模型是底盘,SDK 是车架,MCP 是接口,agent 是车。底盘谁都能造,但能跑得动的整车不多。

原文链接放在第一条评论 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#Anthropic #MCP #Claude #AI工具 #AI日报
