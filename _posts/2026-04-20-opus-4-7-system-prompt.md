---
layout: post
title: "Anthropic 的 system prompt 是公开的。Opus 4.7 上周发布之后，Simon Willison 把 4.6 和 4.7 的 prompt 做了个 diff，能看出来他们在偷偷调几件事。"
date: 2026-04-20 12:00:00 +0800
hero: /assets/opus-4-7-system-prompt/2026-04-20_opus-4-7-clean.png
---

先说最直接的：4.6 里一直挂着一段 "不要说 genuinely、honestly、straightforward" 的 filler 词黑名单，4.7 整段拿掉了。换句话说，Anthropic 觉得 4.7 可以自己管住嘴了，不用再靠 prompt 硬压。

第二个更有意思。4.7 新增了一段 tool_search 指令 —— 意思是，用户问 "你能不能查我日历" 这种事的时候，模型别再顺口说 "抱歉我没这个能力"，先去 tool_search 扫一圈再讲。配套的还有一段新的 act-vs-clarify：能直接动手解决的就别反复问用户。这俩合在一起，看得出 agent 用法已经吃进了默认行为里，不再是 API 那边的专属配置。

系统 prompt 里也第一次明确列出了 Claude in PowerPoint、Claude in Excel、Claude in Chrome 这几个集成。Anthropic 把 "developer platform" 统一改名叫 "Claude Platform"，招牌在收拢。

还有一条简洁度规则，原话是 "focused and concise so as to avoid potentially overwhelming the user"。Opus 本来就以啰嗦著称，这条算是正面回应。

最耐读的反而是儿童安全那段 —— 4.7 新写了一个 critical_child_safety_instructions 块，规定只要拒过一次，后面整段对话都要保持 "极度警惕"。之前没这个 sticky state，应该是内部踩过坑。

看完这份 diff，4.7 的 prompt 更信任模型自己，也更偏 agent，合规那条线收得更紧。没啥震撼发布，但调的地方都是实打实在用的人才会关心的。

原文：https://simonwillison.net/2026/apr/18/opus-system-prompt/

#Claude #Opus47 #AI工具 #AI日报
