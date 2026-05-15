---
layout: post
title: "同一周,Anthropic 和 Thinking Machines 选了完全相反的路线,这件事比任何一个单独的发布都更值得说。"
date: trend 12:00:00 +0800
hero: /assets/1100_thinking-machines-interaction-models/trend_2026-05-13_1100_thinking-machines-interaction-models-hero.png
---

这周二 Anthropic 给 Claude Code 加了 /goal——设一个完成条件,模型自己跑下去,你可以站起来去喝咖啡。同一天,Mira Murati 离开 OpenAI 整整一年后,Thinking Machines 终于把第一份重要工作丢出来,主张刚好相反:别再把人从回路里挤出去。他们叫这套东西 Interaction Models,昨天放出研究预览。

两边都在说"下一代 AI 交互长什么样",但答案差得很远。

人在哪里。Anthropic 押"你可以走开",/goal 整个设计就是让任务跑到结束不用你管。TML 押"你必须留着",他们直接反对"把人当瓶颈推出去"的默认假设——通信带宽不够,不是因为人慢,是因为现在所有 AI 都是回合制,你说完它才看见,它说完你才能插话。

架构。Claude Code 那条路靠 harness——外面拼一层调度,让 turn-based 的模型看起来能自动跑。TML 这次直接训了一个 native interaction model 叫 TML-Interaction-Small,276B 参数 MoE 激活 12B,输入输出全程是流,每 200 毫秒一个 micro-turn,边听边说边看边想。底下还挂了一个异步的 background model 负责深推理,前台保持在场,后台结果出来再无缝插回对话——既不卡顿,也不傻。

能做什么新东西。/goal 解锁的是"无人值守跑完一个复杂任务"。Interaction Models 解锁的是过去靠 harness 拼不出来的:你跑步时它实时数你的配速,你写代码时它看到 bug 直接打断你,你说中文它说英文,两个声音可以同时进行。FD-bench V1.5 拿到 77.8,GPT-realtime-2.0 minimal 是 46.8;轮次切换延迟 0.40 秒对 1.18 秒;Audio MultiChallenge 智能分 43.4,minimal 档的 GPT-realtime 是 37.6,Gemini-3.1-flash-live 才 26.8。这次不是只快,是又快又懂。

TML 也老实承认了瓶颈:长会话上下文还很难搞,276B 已经是当前能实时上的最大尺寸,更大的版本年底前再放。

要选哪边。任务边界清楚、不需要你来回拍板的活——/goal 这条路更省事。要陪你一起想、需要你时不时拐弯改方向的活——TML 押的方向才对得上。说到底这是两种工作方式的赌注:Anthropic 赌模型聪明到不用人盯,Thinking Machines 赌再聪明也得跟人同频。

转给那个还在跟你争 agent 该不该全自动的人。

关注 @svtransit1 · 写给真在用 AI 的人

原文链接放在第一条评论 ↓

#AI #ThinkingMachines #MiraMurati #AI日报
