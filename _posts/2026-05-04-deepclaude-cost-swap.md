---
layout: post
title: "把 Claude Code 后面那条 API 换成 DeepSeek V4 Pro，IDE 里的体验一点没变 —— 作者声称同一套 agent loop，账单便宜十七倍。"
date: 2026-05-04 15:14:09 +0800
source: https://github.com/aattaran/deepclaude
hero: /assets/deepclaude-cost-swap/2026-05-04_1500_deepclaude-cost-swap-hero-raw.png
topic_tags: [claude-code, deepseek, proxy, cost-arbitrage]
---

这个礼拜 HN 首页上来一个 deepclaude，三百多 star。原理其实很 hack：本地代理起在 localhost 一个端口，把 Claude Code 客户端要发去 api.anthropic.com 的请求拦下来，按目标后端格式重发给 DeepSeek、OpenRouter、Fireworks 这些平台，再把对方的回包套回 Anthropic 的 SSE 流式格式塞回去。Claude Code 自己什么都不知道，工具调用、文件读写、git、子 agent 派发，全部照常跑。

作者贴的两个数 —— DeepSeek V4 Pro 在 LiveCodeBench 打出 96.4%、整体推理便宜 17×，都是自报、没第三方复测，先打个问号；但就算砍一半，差距还是够明显。代理本身撑多 backend，Anthropic 可以留作 fallback —— 重活让 DeepSeek 顶，啃不动的边缘 case 退回 Opus，比一刀切换真的省。

老实说我没自己跑过，先码在 todo。但能预判两个坑：一个是 prompt cache —— Anthropic 那套 ephemeral cache 协议是私有的，cache_control 标记和 5 分钟 TTL 过代理转给 DeepSeek 时基本失效，长 context agent 命不中 cache，"便宜 17 倍" 的分母就要重新算。另一个是 tool-use 的严格度 —— Claude 自家模型对 tool schema 不规范的入参、漏字段、多余逗号容忍度很高，开源模型经常会直接报错或者输出乱掉。skill 嵌套深、子 agent 多的工作流跑十来轮之后，崩在 JSON 上的概率明显比官方后端高。

不过这个套路本身比这个 repo 重要 —— Claude Code 的 loop 被人在外面截下来过一次，模型这一截就开始商品化了。Anthropic 的护城河从来不在 API 上，而是那条 agent loop 本身。Max 那张价签撑得住多久，就看下半年第三方复测。

原文链接放在第一条评论 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #DeepSeek #AI工具 #LLM
