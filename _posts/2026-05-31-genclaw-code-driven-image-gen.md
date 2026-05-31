---
layout: post
title: "【AI 画图,能不能先「写代码」再渲染?】👆"
date: 2026-05-31 15:14:00 +0800
source: https://arxiv.org/abs/2605.30248
hero: /assets/genclaw-code-driven-image-gen/2026-05-31_1500_genclaw-code-driven-image-gen-hero.png
topic_tags: [genclaw, image-generation, code-driven, tencent, research]
---

现在的 AI 画图基本是黑箱:写 prompt,它「抽卡」似的吐一张,想改个细节只能换措辞再抽。腾讯混元这两天放出的 GenClaw,提了个反直觉的思路——让模型先写一段可执行的代码(SVG / HTML / Three.js),渲染成「视觉草图」,再往下走。

像人真画画那样分三步:构思 → 勾线 → 上色。论文里一句话挺到位:代码,是连接「语言推理」和「像素合成」的一块可控中间画布。

绕这一圈图什么?就图「可控」:

🔧 改代码就能改图,不用整张重抽

🔁 同一段代码每次渲染都一样,不像扩散每次带随机

⚠ 但说清楚:这是范式 / 概念论文,摘要里没放 benchmark、没开 GitHub、也没 demo——现在是个「值得想一想的方向」,还不是能直接拿来用的工具,能不能打过现在的扩散模型,得等它放结果。🧐

你觉得「AI 写代码来画图」,是噱头,还是真方向?

关注 @svtransit1 · 写给真在用 AI 的人

🔗 GenClaw 论文(arXiv)· 第一条评论取 ↓

#AI #图像生成 #AIGC #腾讯混元
