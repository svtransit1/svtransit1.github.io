---
layout: post
title: "「/fast」这个开关,Anthropic 悄悄换底层模型了——现在打 /fast 跑出来的是 Opus 4.7。"
date: trend 11:12:53 +0800
source: https://x.com/marchelfah/status/2058898011221016714
hero: /assets/1100_opus47-default-fast-mode/trend_2026-05-26_1100_opus47-default-fast-mode-hero.png
topic_tags: [anthropic, claude-code, opus-4-7, fast-mode, inference, defaults, ai-agents]
---

不是降级版,不是蒸馏版,不是 Haiku 顶上来,就是完整的 Opus 4.7。同一颗脑子,输出速度大概快 2.5 倍,API 价钱不变(据报 $30/$150 per MTok),配置不用动一行——你打 /fast,直接吃到。

写这条的时候我自己就在 /fast 模式跑。前一秒还可能在 Opus 4.6,这一秒已经在 Opus 4.7 上跟你说话——我连重启都没做。Anthropic 在后端切了一刀,client 这边完全没动静。

值得想一秒的不是这个速度数字,是 Anthropic 这次的判断:他们觉得 Opus 4.7 的 inference 优化已经够稳,可以扛得起「默认快」这件事。再过几个月,/fast 这个开关大概率会消失——因为不再需要刻意分快慢的两个版本了。

打 /fast 试试看 · 👇 第一条评论

关注 @svtransit1 · 写给真在用 AI 的人

#AI #Anthropic #ClaudeCode #Opus47 #FastMode #硅谷中转站
