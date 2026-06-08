---
layout: post
title: "Anthropic 的 Boris Cherny——Claude Code 背后那个人——刚发了条推,讲怎么让 Opus 自己跑上几个小时、甚至几天,去啃一个大任务。五条都挺实操的,顺手给你记下来 🧐"
date: trend 11:14:30 +0800
source: https://x.com/bcherny/status/2063792263067754658
hero: /assets/1100_opus-autonomous-long-tasks/trend_2026-06-08_1100_opus-autonomous-long-tasks-hero.png
topic_tags: [opus, claude-code, autonomous-agents, long-running-tasks]
---

他开场说:现在有不少 benchmark 显示,Opus 是跑「长任务」最强的模型。然后给了五个让它自主运行的技巧。

一,权限开 auto 模式,让 Claude 别一步一确认地老打断你。

二,用 dynamic workflows,让 Claude 自己去编排成百上千个 agent,把任务拆着做完。

三,用 /goal 或者 /loop,推着它一直干到真正完成,而不是干一半就停。

四,把 Claude Code 跑在云端,这样你合上笔记本也不耽误——最省事的是用桌面或手机 App。

五,给它留一条能端到端自检的路,比如装上 Claude 的 Chrome 浏览器扩展,让它自己回头验一遍成果对不对。

五条连起来看,是一套「让模型自己负责到底」的打法:你定目标、给权限、留一条自检的路,剩下的让它自己跑 ⚡ 其中我觉得最关键的是第五条——自检。一个任务要跑几个小时,中间错一步,后面全跟着歪;有没有一条能让它自己回头验、自己纠的回路,基本决定了这事能不能真的放手。

提醒一句:这是 Anthropic 自己人给的用法,天然偏向 Claude 那套工具链;尤其 auto 权限放开之前,先想清楚它手上能碰到什么。但「让 agent 自主跑长任务」确实是这半年最明显的方向,值得照着试一遍。

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #Opus #AIagent
