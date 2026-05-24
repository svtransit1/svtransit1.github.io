---
layout: post
title: "「unlock the car」「turn on dog mode」——这两行命令,现在能直接在 Claude Code 里跑了。"
date: trend 17:29:22 +0800
source: https://x.com/mvanhorn/status/2058189714088456687
hero: /assets/1100_tesla-claude-code-skill/trend_2026-05-24_1100_tesla-claude-code-skill-hero.png
topic_tags: [tesla, claude-code, agent-skills, ppressdev, mvanhorn, openclaw, hermes, ai-agents]
---

@ppressdev 这两天把一个 Tesla CLI / Claude Code Skill 推上线,demo 视频在 X 上一晚拿了 6 万多浏览,407 个 bookmark。做的事说穿了就一句话:把 Tesla 自家 app 里那些天天要点的操作,扔进 Claude Code 的 Skill 系统,让 agent 直接调。

具体放进去的能力——

1. 一句话解锁:跟 Claude 说「unlock car」,不用掏手机点 app

2. 一句话开 dog mode:出门买咖啡前甩一句「dog mode on」

3. 定时 agent:写一条「每个上学日早上 7:50 帮我把车解冻好」,agent 自己每天跑

4. 充电账本:每次充电的电费自动入账,月底一张表

5. Supercharger 排队监控:目的地充电桩满了就推送一条到手机

这事值得看的地方不在「能用 CLI 控制 Tesla」——Tesla 的 REST API 已经存在很多年,各种 wrapper 满天飞。值得看的是这套东西的封装方式:把它做成一个 Claude Code Skill,意味着 Claude(或者任何 agent)可以把车的状态当成上下文,跟你的日历、邮件、待办一起推理。

举个具体的:agent 看到日历明天早上 8 点会议,自动算回早上 7:40 该解冻——你不用预设规则,agent 凭已有上下文自己决定。这就是 skill 化跟纯 API 化的差别——一个能推理上下文,一个只能被调用。

代码挂在 printingpress.dev,Tesla 这个 device library 是 https://printingpress.dev/library/devices/tesla,还有 OpenClaw 和 Hermes 两个 skill 版本,选你自己的 agent 栈接进去。

更大的信号是:agent skills 这条线开始有人往「真实物理世界」推。过去半年大部分 skill 都还是软件工具(GitHub、Slack、Notion 这些)。Tesla 是第一个公开的「我家车也接进来了」的样板。下一个大概率是智能家居、智能门锁、然后是机器人——这条线一旦打通,agent 的实用边界就从屏幕里跑出来了。

转给那个一直在等 AI agent「真正能做事」的朋友——这就是「真正能做事」的样子。

更多 device skills · 👇 第一条评论

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #Tesla #Agent #Skills
