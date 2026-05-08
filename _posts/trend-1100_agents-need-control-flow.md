---
layout: post
title: "「Agent 缺的不是更多 prompt,是控制流。」"
date: trend 11:09:19 +0800
source: https://bsuh.bearblog.dev/agents-need-control-flow/
hero: /assets/1100_agents-need-control-flow/trend_2026-05-08_1100_agents-need-control-flow-hero-raw.png
topic_tags: [agent, control-flow, prompt-engineering, brian-suh, software-architecture]
---

这是 Brian Suh 在 bsuh.bearblog.dev 这周写的一篇短文,HN 拿了 349 分。我看完后一直在想他那句最狠的总结。

他的论点是这样的:在 prompt 驱动的系统里,「statements are suggestions」——你写下的指令对模型来说只是建议,不是约束。这就是为什么开发者最后都会写出全大写的「MANDATORY: …」「YOU MUST …」「DO NOT EVER …」这种像在喊话的 prompt。喊得越大声,越能感觉到自己在跟一个不愿意听话的协作者较劲。

跟传统代码相比,prompt 真正缺的是确定性,表达力反而绰绰有余。代码里 if 就是 if,return 就是 return,模块化设计带来本地推理能力——你看一个函数,就能知道它在干啥,不用读整个仓库。

Brian 的处方是:把 LLM 当作模块里的一个组件,塞进确定性的脚手架里,而不是让 LLM 当系统的主控。这样可调试、可测试、可组合。

我看下来感觉是这样:这跟昨天 Stanford AI Index 那个 SWE-bench 跑到 100% 的现象是一对硬币。模型能力够了,但生产环境要的是「每次调用都是同一种行为」,这事 prompt 给不了你,代码可以。

下半年好的 agent 框架,大概率会越来越像传统软件库——LLM 是其中一颗芯片,不是 CPU。

来源 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AIagent #Claude #ClaudeCode #软件工程 #AI工具
