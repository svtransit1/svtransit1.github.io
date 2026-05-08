---
layout: post
title: "DeepMind 这周更新了 AlphaEvolve 的影响力报告。一年时间,这个 Gemini 驱动的进化式编码 agent,已经在十几个领域跑出可量化结果。我把里面最硬的几条拎出来。"
date: 2026-05-08 12:00:00 +0800
hero: /assets/alphaevolve-impact-broadcast/2026-05-08_1300_alphaevolve-impact-broadcast-hero.png
---

先解释结构。AlphaEvolve 整体是一个 ensemble,不是单点模型:Gemini Flash 负责广度——快速生成各种想法;Gemini Pro 负责深度——给每个想法挑刺、加洞察。中间加一个进化算法做选择压力,加一个自动验证器测每个候选方案。整个系统能解的问题只有一个约束:解必须能被算法描述,且能被自动验证。

数学层面的成绩单。50 道开放数学问题里,75% 重新发现已知 SOTA,20% 直接刷新 SOTA。最被讨论的是矩阵乘法——它发现了一种用 48 次标量乘法做两个 4×4 复矩阵相乘的算法。这是 Strassen 1969 年那篇经典论文之后,56 年来第一次有人在这个设置上把数字往下压。

工程落地这边数字更硬。基因组学:让 PacBio 的 DeepConsensus 测序变异检测错误率下降 30%。电网优化:AC 最优潮流问题的可行解比例,从 14% 拉到 88%。量子物理:Google Willow 处理器的量子电路错误率降到原来的十分之一。这条路线还在跟陶哲轩合作攻击 Erdős 问题、TSP 上界、Ramsey 数。

商业部分。Klarna 的 transformer 训练速度翻倍;Substrate 的光刻 runtime 提升数倍;FM Logistic 路由效率 10.4%,一年省 1.5 万公里;WPP 广告投放精度 10%;Schrödinger 的机器学习力场计算 4×。Google 自家拿它优化了 TPU 硬件、Spanner 写放大降 20%、编译器存储节省 9%。

我看下来感觉是这样:过去一年大家关注的 AI 故事是「模型考多少分」。AlphaEvolve 这条线在讲完全不同的事——AI 已经能独立做出真正的科学发现,而且可以被工业界直接采购、直接计入财报。Strassen 算法 56 年没人动,2026 年被一个 agent 改写——这种层级的变化,benchmark 跑分捕捉不到。

下半年真正值得看的提问已经从「哪家模型分更高」转成「哪家公司用 AI 跑出了一项五年内不会被仿制的工程红利」。

来源 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AlphaEvolve #DeepMind #Gemini #AI科学发现 #AI工具
