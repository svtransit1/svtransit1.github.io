---
layout: post
title: "你同时在用 Claude Code、Codex、Pi……还各自一套配置、一套权限——管得过来吗?有人做了个\"总管\",叫 Omnigent。一张图,看懂它站在哪 👇。"
date: 2026-06-14 15:11:42 +0800
source: https://github.com/omnigent-ai/omnigent
hero: /assets/omnigent-agent-meta-harness/2026-06-14_1500_omnigent-agent-meta-harness-hero.png
topic_tags: [omnigent, ai-agents, agent-harness, claude-code, open-source]
---

🔝 最上面那层,就是 Omnigent。不管你底下挂的是哪个 harness,它都能统一接管;想换模型、换 agent,基本一行的事,不用重写。

🛡 中间是"策略闸":能跑什么 shell、能不能改文件、一次最多烧多少 token——全在服务端按规则卡死,靠的是策略,不是提示词里求它自觉。

👥 底下是协作:多人能实时盯着同一个 session,旁观、接手、甚至 fork 一条对话各走各的,终端、网页、手机还能同步。

说清楚 ⚠️:它还很早期(Apache 2.0 开源,目前六百多 star、二十几个 commit),也不是 Databricks 的官方项目(Databricks 只是它可选的模型源之一)。先别当成标准,当个有意思的方向看。

agent 越用越多、越用越乱的人应该懂:真正缺的,可能不是又一个更强的 agent,而是一个能把它们都管起来的"总管"。

项目地址 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #AIagent #ClaudeCode #开源 #Omnigent
