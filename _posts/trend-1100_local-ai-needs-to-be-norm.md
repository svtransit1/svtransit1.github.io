---
layout: post
title: "HN 上有一篇 657 分的博客在吵一件事:Local AI 该变成默认设置——你的 app 该把它当 baseline,而不是当稀奇玩法。作者用一个真在跑的 iOS app 当证据,顺手把 Apple 的 FoundationModels 那套东西放进了讨论中心。"
date: trend 11:12:00 +0800
source: https://unix.foo/posts/local-ai-needs-to-be-norm/
hero: /assets/1100_local-ai-needs-to-be-norm/trend_2026-05-11_1100_local-ai-needs-to-be-norm-hero-raw.png
topic_tags: [local-ai, apple-foundationmodels, on-device, privacy, swift]
---

四个论点,排出来不复杂。

**1. 隐私靠政策只是表面,靠架构才彻底。** 数据上云就有 retention、consent、audit、breach、政府要数据、训练数据混入等等一大堆问题等着你。在设备里跑掉一切,这堆问题压根不存在。这一条最朴素,但最难被「写隐私政策」这种动作替代。

**2. 云依赖就是分布式系统,得自己背账单。** 你以为是「调一下 API」,实际是把外部供应商的 uptime、rate limit、账单、政策变化全部纳入你应用的故障面。本地跑没有这些,网络断了照常运行。

**3. 设备上有空闲算力,是你没用。** Neural Engine、GPU、张量加速器,iPhone / Mac 上跑得动 9B 量级模型已经是常态。你掏钱买的硬件大多数时间在 idle,云端那边却在数你的 token。

**4. 任务有边界,匹配本地模型刚好。** Summarize、classify、extract、normalize、rewrite——这几类是绝大多数 LLM 实际工作量,本地模型完成度足够。需要超人 PhD 级智能那种少数 case,留给云端。两套放在一起,体验更稳。

案例是作者自家的 Brutalist Report iOS 客户端。新闻聚合 app,加了一个可选的「intelligence」视图:每篇文章自动生成摘要,完全在设备上跑,不联网、不上日志、不挂账户。技术栈也都点出来了——Apple FoundationModels 框架,LanguageModelSession 跑推理,Swift 用 @Generable 装饰器加 @Guide 注解,直接拿到结构化字段输出。整套东西免费、内置,iOS 18+ 都能用。

我看完一遍,觉得最大的转向不在技术上,在叙事上。过去两年「AI 工程师」基本等于「云调用工程师」,大家被训练成默认掏钱、默认订阅、默认上传上下文。Apple 这一步——把 FoundationModels 装进系统,免费给开发者——是把这个默认值反过来,放回设备端的第一次正式动作。云不会消失,但「云优先」这件事开始松动。

来源 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #本地LLM #Apple #FoundationModels #AI日报
