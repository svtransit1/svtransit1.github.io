---
layout: post
title: "OpenAI 干了件有点反直觉的事：它出了个官方插件，专门让你在竞争对手的 Claude Code 里，调用自家的 Codex。😏"
date: 2026-07-10 18:15:00 +0800
source: https://github.com/openai/codex-plugin-cc
hero: /assets/codex-plugin-cc-second-opinion/2026-07-10_1800_codex-plugin-cc-second-opinion-hero.png
topic_tags: [claude-code, codex, openai, cross-model-review, tooling]
---

这插件叫 codex-plugin-cc，7 月 8 号放出来的，两天在 GitHub 冲到 27.3k 星。功能一句话说清：你人还在 Claude Code 里，需要的时候把活儿甩给 Codex——让它审代码、或者接手一个任务去跑。

「能互调」只是表面。往下想一层：OpenAI 为什么要这么做？它没去抢 Claude Code 那个顶层 CLI 的位置，转头把 Codex 塞了进去，当一个"审查 + 打杂"的 sub-agent。CLI 门面这层的仗，OpenAI 基本是让了；它盯上的，是"第二意见"那个位置。

装完之后，你手上会多出八个 /codex: 命令。挑几个最值钱的说👇

· /codex:review — 让 Codex 审一遍你（或 Claude）刚写的代码

· /codex:adversarial-review — 让 Codex 开"挑刺模式"做对抗性审查。这个思路我觉得最有意思：Claude 写、Codex 专门找茬，两个训练口味完全不同的模型，互相补对方的盲区

· /codex:rescue — 把一整个任务直接甩给 Codex 后台去跑

· /codex:transfer — 开一条常驻的 Codex 线程，接着往下聊

· 剩下 /codex:status、/codex:result、/codex:cancel 管那些长时间任务，/codex:setup 用来确认装没装好

跨模型审查这件事，价值不在花哨。以前你想让另一个模型帮你看一眼，得手动把代码复制到别的工具里再问一遍；现在一条命令的事。Claude 和 Codex 的训练数据、脾气都不一样——一个觉得没问题的地方，另一个可能一眼就看出坑。这种"第二双眼睛"是能省你 bug 的。

实际用起来节奏大概这样：写完一段自己都有点没底的代码，先 /codex:review 过一遍图个心安；真正拿不准、或者改动很大的地方，直接上 /codex:adversarial-review，让它往死里挑，挑不出来你才敢合。手上有个耗时的重构、或者一堆测试要跑，/codex:rescue 甩到后台，你这边接着写别的，回头 /codex:result 收货就行。安装走 Claude Code 插件那一套，装完先 /codex:setup 确认授权通了再动手。

但有两点得先摆明。一，这是 OpenAI 自己的插件，"有事来我这审一下"这套说法，它当然希望你买账。二，你的代码从此两家都经手了——Anthropic 和 OpenAI 各看一遍，对不能外传的项目，这条得先想清楚再装。

所以值不值得装？如果你本来就吃住在 Claude Code 里，又不介意代码过两家的手，光 /codex:adversarial-review 这一个命令，大概就够回本。真正该记下的，是它背后那个信号：CLI 的门面之争差不多翻篇了，接下来大家抢的，是"谁来当那个替你复核代码的第二个模型"。🧐

转给那个天天泡在 Claude Code 里写代码的朋友——这命令他会想装。

关注 @svtransit1 · 写给真在用 AI 的人

链接 · 👇 第一条评论

#AI #ClaudeCode #Codex #AI工具
