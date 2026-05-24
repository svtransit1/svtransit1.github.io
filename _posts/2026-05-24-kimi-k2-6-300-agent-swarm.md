---
layout: post
title: "Moonshot AI 一个月前在 Kimi K2.6 里塞了一个 300 个 sub-agent 的并发系统——单次自主任务跑 4000 步,持续编码 13 小时。完整模型开源在 HuggingFace 上,Modified MIT。"
date: 2026-05-24 09:09:10 +0800
source: https://kimi-k2.org/blog/24-kimi-k2-6-release
hero: /assets/kimi-k2-6-300-agent-swarm/2026-05-24_0901_kimi-k2-6-300-agent-swarm-hero.png
topic_tags: [kimi, moonshot-ai, agent-swarm, open-weights, moe, china-ai]
---

底层是 1 万亿参数的 MoE,每个 token 激活 320 亿。256K context。原生 INT4 量化,意思是即便是消费级显卡用户,跑起来也比同档体量轻得多。

GPQA-Diamond 上拿到 90.5——比 GPT-5.4 的 92.8 差 2.3 分;但是开源、可商用、可本地跑这三件事,GPT-5.4 一项都没有。

「agent swarm」具体是什么?上一代 K2.5 是 100 个 sub-agent、1500 步上限;K2.6 直接拉到 300 个 sub-agent、4000 步,而且可以连续跑 13 小时不掉线。这不是单 agent 跑长一点——是用 300 个领域专精的小 agent 并发协作,真正在做的事更接近一个团队。

中文圈 AI 这两年讨论最多的问题之一是「开源 frontier 模型还差多远」。K2.6 给的答案是:差 2.3 分(在最难的基准上)+ 不带许可证束缚。这两件事的组合,大概是 frontier 开源最有意义的当下版本。

转给那个还觉得开源模型差一截的同事——差距只有 2.3 分。

链接 · 👇 第一条评论

关注 @svtransit1 · 写给真在用 AI 的人

#AI #Kimi #MoonshotAI #开源模型 #agent
