---
layout: post
title: "🐑 你有没有同时开着三四个 Claude Code,然后彻底搞不清哪个卡住了、哪个在瞎跑?"
date: 2026-07-19 09:19:41 +0800
source: https://github.com/ogulcancelik/herdr
hero: /assets/herdr-agents-orchestrate-agents/2026-07-19_0900_herdr-agents-orchestrate-agents-hero.png
topic_tags: [claude-code, agents, orchestration, terminal, dev-tooling]
---

这几乎是每个认真用 coding agent 的人都会撞上的墙。模型越来越能自己干活,你就越想同时多开几个——可一旦超过两三个,你就从「写代码的人」,悄悄变成了「在一堆终端窗口之间来回切的调度员」。

GitHub 上最近有个项目专门治这个,叫 Herdr,已经 18k star。它把自己定位成「一个住在终端里的 agent 多路复用器」——说白了,就是把 tmux 的思路,重新为「每个窗口都是一个自主 agent」这件事做了一遍。

🖥️ 它解决的痛点很具体:一屏看全每个 agent 是卡住了、在干活、还是干完了,而且给你看的是它真实的终端画面,不是被包装、总结过的二手信息;断开也不丢——detach 之后 agent 继续跑,你从任何一台终端、甚至 SSH 过去都能重新接上,重启也不掉 session;整个东西就一个 Rust 二进制,没有 Electron,在你现在用的终端里直接跑。

🔌 但真正让我觉得有意思的,是它多走的那一步:它开了一个纯 socket API,让 agent 自己也能用 Herdr——agent 可以自己开窗口、读另一个 agent 的输出、等另一个干完再动。举个场景:一个 agent 写代码,另一个盯着它跑测试,测试一挂就自动叫醒第三个来修——整条流水线不用你在中间手动串。

发现没有?这一步,把「人盯着一堆 agent」推到了「agent 自己在编排 agent」。

💡 我的判断:大家还在比谁家模型更聪明,可真正天天跑 Claude Code、Codex 的人都知道,卡人的地方早就从「单个 agent 强不强」,挪到了「同时开五个怎么不失控」。18k star 说明这个痛点有多普遍。单 agent 的性能内卷快到头了,下一个护城河,是编排。

你现在同时开几个 agent?开到几个,就开始管不过来了?

转给那个同时开一堆 Claude Code、快管崩了的朋友。

关注 @svtransit1 · 写给真在用 AI 的人

完整链接 · 评论区取 ↓

#AI #ClaudeCode #AIagent #开发工具 #AI日报
