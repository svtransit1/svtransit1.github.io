---
layout: post
title: "《The Bottleneck Was Never the Code》——这周 HN 442 分,作者匿名,thetypicalset.com 出的一篇短文。值得花十分钟读完,我把核心论点拆给你看。"
date: 2026-05-07 12:00:00 +0800
hero: /assets/bottleneck-was-never-code/2026-05-07_0900_bottleneck-was-never-code-hero-raw.png
---

过去两年讨论 AI coding,大家爱说「coding 速度提升十倍」。文章直接把这个叙事拆了:写代码从来不是软件团队的瓶颈。

作者举了几个具象例子。一个被推迟一年的 structured-generation 实验,他用 Codex 几个小时就跑出原型。但产品没因此提前一年交付——那一年被卡住的环节是「要不要做、做哪一版、和谁对齐」,跟写代码无关。代码便宜下来之后,瓶颈往工程师上游搬:在 product / management / spec 那一层。

文章引了 Jevons 悖论做类比。煤变便宜不会让用煤的总量下降,反而上涨。代码变便宜也一样——团队会做更多功能,而不是更少。但用户能消化的功能数量没变,所以挑选要做什么的纪律,变得比写代码的纪律重要。

还有一个观察我特别想拎出来:Context is the commodity an organization runs on。Agent 拿不到上下文——它没办法像人那样在饮水机旁边吸收业务背景、历史决策、组织里那些没写在 doc 里的东西。所以未来组织的护城河转移了:从技术先进转到「能不能把隐性知识显性化、可被 agent 调用」。

作者最后给了一个具体的方向:让 agent 跑 loop 去从代码库、PR、内部 IM 里抽取并合成隐性上下文,把组织的一致性当成一件可以建造的东西,而不是「同事坐得近就自然形成」的副产物。

我看下来感觉是这样:2026 年 AI 圈的话术正在分层。表层在比"模型快不快、便宜不便宜",底层真正决定输赢的,是哪家公司能把 spec 写清楚、能把 context 显性化、能让上游决策不再是阻塞下游的那道墙。

代码便宜了,但没人能让"想清楚"也跟着便宜。

来源 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #软件工程 #AI叙事 #AI工具
