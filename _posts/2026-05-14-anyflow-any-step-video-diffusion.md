---
layout: post
title: "\"我用 consistency-distilled 视频模型,加 sampling step 怎么画质反而变差?\"
date: 2026-05-14 12:00:00 +0800
hero: /assets/anyflow-any-step-video-diffusion/2026-05-14_2000_anyflow-any-step-video-diffusion-hero.png
---

不是你的设置不对,这是这类模型的"暗病"。Consistency distillation 训练时只优化"少步数下的画质上限",于是模型把全部能力都压在 4 步、8 步那个 narrow window 上;一旦你想加步数想拿更精细的画面,反而踩进了它没见过的 region,误差累积,画质退化。这件事 video gen 圈一直心知肚明,但没几个人愿意正面写。NVIDIA 这周挂的 AnyFlow 论文把这个 trade-off 说清楚,然后给了 fix。

作者团队是 Yuchao Gu、Song Han、Mike Zheng Shou 这一组(NVIDIA),思路是把"教徒弟"的方式换了:传统 consistency distillation 是"端点对齐"——只让学生模型在固定步数终点跟老师一样,中间过程不管。AnyFlow 改成"全程对齐"——把 ODE sampling 的整条轨迹优化下来,任意切多少步都对得上。

具体方法叫 Flow Map Backward Simulation:把完整的 Euler rollout 拆成一段段 shortcut transitions,每一段都可以作为训练单元。这样既减少 discretization error,又压住 exposure bias(学生跑偏后越跑越歪的老问题)。

在 1.3B 到 14B 参数四个规模上都测了。论文里一句话挺关键:"少步数 regime 下跟 consistency-distilled 基线打平或超过,多步数 regime 下还能继续涨"——意思是你以前要么选"速度",要么选"画质",AnyFlow 提议两个都不用让。

下一波视频生成模型如果都走这条路,大家终于可以不用再纠结"step 数到底设多少"了。

关注 @svtransit1 · 写给真在用 AI 的人

完整链接 · 评论区取 ↓

#AI #视频生成 #扩散模型 #NVIDIA #AnyFlow
