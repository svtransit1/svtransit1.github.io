---
layout: post
title: "想让 AI 帮你判断「这个 idea 到底靠不靠谱」?有个新研究给你提个醒:它大概率会说「靠谱」——哪怕那个 idea 根本不行。😬"
date: 2026-05-31 21:16:00 +0800
source: https://arxiv.org/abs/2605.30329
hero: /assets/soundnessbench-llm-optimism-bias/hero.png
topic_tags: [soundnessbench, llm-limits, optimism-bias, evaluation, research]
---

这两天 arXiv 上有篇 SoundnessBench,干了件挺损的事:从 ICLR 的投稿里重构出 1099 个机器学习研究 proposal,人工标好「方法论靠不靠谱」,然后丢给 12 个前沿大模型,让它们当评审。

结果挺一致:这 12 个模型都有「乐观偏差」——经常把明明不靠谱的 proposal 也评成「靠谱」。假阳性一大堆,等于闭着眼往「行」的方向夸。

想救一下?研究者试着「更狠地 prompt」逼它严格点,结果只是把错误从「假阳性」翻成了「假阴性」——从无脑说行,变成无脑挑刺,还是不准。论文结论说得很直白:现在的大模型,还当不了「科研严谨性」的独立首轮把关人。

这研究测的是科研 proposal,但对每天用 AI 的人,提醒是通用的:🧐 AI 很适合帮你「生想法、补盲点、列可能性」,可「这想法到底成不成立」这种判断,别让它一个人拍板——它被调得太想讨好你,默认就偏向说「不错」。把它当顾问,别当裁判。

你有没有被 AI 一句「这个想法很好」忽悠过,回头发现根本走不通?

转给那个习惯让 AI 帮自己拍板的朋友。👇

关注 @svtransit1 · 写给真在用 AI 的人

📄 SoundnessBench 论文(arXiv)· 评论区取 ↓

#AI #大模型 #AI局限 #AI评审
