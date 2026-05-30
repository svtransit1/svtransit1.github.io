---
layout: post
title: "Elon 凌晨发推: SpaceX 自己写的 AI 训练 stack 比 JAX 快一个数量级以上。🚀⚡"
date: trend 12:00:00 +0800
hero: /assets/1700_spacex-c-training-stack-10x-jax/trend_2026-05-28_1700_spacex-c-training-stack-10x-jax-hero.png
---

原文很直接 (3.3M 浏览, 2 小时前):

「SpaceX 的 in-house AI training stack V1.0 快写完了。用 C 写的, 精确映射到 220K 张 GB300, 配 800G NIC, 重度 pipeline parallelism, 尽可能贴近裸金属。

相比 JAX 在大规模训练上的潜在加速幅度 — over an order of magnitude。」

3 个轴的对比:

① 抽象层级 · Python vs C

JAX 是 Python 上的 XLA + autograd 封装, 灵活、生态广。SpaceX 直接拿 C 写, 跳过 Python runtime + JIT 编译开销, 每条指令都接近硬件意图。

② 硬件适配 · 通用 vs 专项

JAX 设计是「适配多种加速器」, 抽象层级高。SpaceX 这套是「我有 220K 张 GB300 + 800G NIC, 我就只优化这个」, 用 pipeline parallelism 把训练分布得尽可能均匀。

③ 性能 · over an order of magnitude

Elon 说的是 ≥10×。注意限定词: 「在大规模训练上的潜在加速」。小模型、小集群你跑不出来这个优势, 这套是为 frontier model 量级训练设计的。

谁该转过去用?

- 220K 卡 + 800G NIC 这种规模的实验室 → 必须考虑

- 100~1000 张卡的研究团队 → JAX/PyTorch 仍然合理, 切换成本高于收益

- 个人 / 小团队 → 离这个工具差几个数量级, 看就好

这事的份量在「Elon 正式承认 SpaceX 在做 frontier AI 训练 stack 自研」。之前都是 xAI 那边的话题, SpaceX 这一手出来, 直接拉到「火箭公司自己训自己的 AI 模型」的画面。

可以猜的是: 这个 stack 之后大概率会用在 Grok 训练上, 或者更下一代 xAI 模型上, 也可能跟 Starlink-side 的 inference workload 联动。

下一年「大公司自研训练 stack」这条赛道, NVIDIA NeMo / Meta PyTorch / DeepMind JAX / xAI SpaceX-stack 四方对垒, 越来越好看。

转给那个还在调 JAX TPU mesh 的朋友 👇

关注 @svtransit1 · 写给真在用 AI 的人

🚀 Elon Musk 原贴 + GB300 / 800G NIC 技术规格 · 评论区取 ↓

#Elon #SpaceX #xAI #GPU训练 #AI基础设施 #JAX
