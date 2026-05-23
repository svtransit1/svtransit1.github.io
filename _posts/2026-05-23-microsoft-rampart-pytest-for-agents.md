---
layout: post
title: "Microsoft 给 AI 智能体出了一套 pytest——还能直接跑在 CI 里。"
date: 2026-05-23 12:11:57 +0800
source: https://www.microsoft.com/en-us/security/blog/2026/05/20/introducing-rampart-and-clarity-open-source-tools-to-bring-safety-into-agent-development-workflow/
hero: /assets/microsoft-rampart-pytest-for-agents/2026-05-23_1203_microsoft-rampart-pytest-for-agents-hero.png
topic_tags: [microsoft, rampart, ai-agent, pytest, agent-safety, prompt-injection, open-source]
---

它叫 RAMPART,5 月 20 号开源在 github.com/microsoft/RAMPART,建在 Microsoft 自己的红队框架 PyRIT 之上。用法很朴素:把一个对抗场景——比如 agent 读到一封带 prompt injection 的邮件、读到一个被污染的工单——写成 pytest 测试用例,跑在 CI 里,直接给 pass/fail。

但真正让这个东西能落地用的,是它的统计模式。你可以定一条规则:「这个 agent 动作,在 1000 次重跑里至少要安全 80%」。单跑一次 demo 看不出来的问题,1000 次统计是挡得住的。评估器本身是 composable 的——会看 agent 调用了哪些工具、产生了什么副作用、有没有越出预期的边界。

配套还有一个工具叫 Clarity,跟 RAMPART 互补:不是测试用的,是写代码之前先把「我们到底要做什么」想清楚——文档塞到 .clarity-protocol/ 目录,几个 AI thinker 分别从安全、人因、对抗、运维四个视角审一遍,然后跟 repo 一起进 git。

Agent 测试这块一直是手工 demo 和直觉评判;Microsoft 这一手,把它推到 pytest 这个最低门槛的工程惯例上。开源 + 跑在 CI 里 + 统计阈值——这三件事一起做,基本是把 agent 安全从研究领域拽到 SRE 那一头去了。

转给那个在做 agent 评测的工程师同事——他可能等这个工具等了一年。

原始出处 · 第一条评论拿

关注 @svtransit1 · 写给真在用 AI 的人

#AI #AIagent #Claude #开源 #AI安全
