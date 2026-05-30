---
layout: post
title: "医学影像 AI 今天上了一份你大概率没看到、但接下来一年所有做计算病理的人都得读的论文——SpaPath-Bench,中科院自动化所 (Tianzi Jiang 团队) + 合作者把 19 个病理基础模型 (Pathology Foundation Model) 拉到一张桌子上,跑了 83K 次评估,问一个被业内忽略很久的问题:这些模型到底在「看」什么?🔬"
date: 2026-05-26 21:22:18 +0800
source: https://arxiv.org/abs/2605.25764
hero: /assets/spapath-pathology-foundation-models/2026-05-26_1930_spapath-pathology-foundation-models-hero.png
topic_tags: [medical-ai, computational-pathology, foundation-model, benchmark, arxiv, tianzi-jiang, pathology-fm, whole-slide-image, spatial-transcriptomics]
---

#病理FM这一年长出来了——但没人量过它们的「空间感」 🧬

CLIP、SAM 这类视觉基础模型过去两年在通用图像上跑得飞起;医学方向的对应物——病理基础模型 (PFM)——也跟着 explode 了。19 个开源/半开源 PFM,每一个都说自己能从 whole slide image (一张几十 GB 的显微镜大图) 学到通用表征。

问题是:之前所有的 benchmark 都是「下游临床任务对不对」——给一个 PFM 接一个分类头,看它能不能识别肺癌 / 乳腺癌 / 转移灶。这种测试有用,但它只告诉你「这个模型作为黑盒,跑这条线行不行」。不告诉你它的 embedding 到底学到了什么。

#SpaPath-Bench直接量表征,跳过任务层 🔍

SpaPath-Bench 不接分类头。它直接拿 PFM 输出的 embedding,丢去做「空间结构识别」(SDI, spatial domain identification)——能不能在一张全切片里,把不同的组织区域 (肿瘤区 / 间质区 / 免疫浸润区) 按它们各自的分子表达分清楚。

这个任务为什么戳到点子上?🎯

做空间区域识别需要的不只是「这是一块上皮组织」——还要捕捉到这块上皮和它周围的间质形成什么关系。一个 embedding 真的学到了组织空间架构,这个任务就跑得好;只学到了形态学纹理,跑这个任务就掉链子。embedding 的「空间感」第一次有了一把可量化的尺子。

#跑的规模——83K次评估 📊

📊 19 个 PFM encoder

📊 7 种 SDI 方法

📊 42 张配对的 WSI + 空间转录组数据

📊 3 套评估标准:无监督空间一致性 / 转录组参考一致性 / 专家参考一致性

📊 总计 83K 次实验

这个体量基本上是病理 FM 评估侧第一次有像样的对照实验。

#反直觉的结论 💡

「不同的预训练范式,捕捉的是组织空间架构的不同侧面。」

意思是:没有「最好的 PFM」这种东西。一个在 MIM (Masked Image Modeling) 预训练上跑得好的模型,捕捉的空间信息和一个在对比学习上跑得好的模型,根本就不在同一个维度。下游任务里看似可互换的 19 个 PFM,在表征层面其实分裂得很厉害——这一点过去因为大家只看任务级 metric,完全没人注意到。

#为什么AI-builder该读一下 🏗️

🏥 病理 FM 这一年正在从「学术 toy」往「医院真的会上的工具」靠

🧪 这套 representation-level benchmark 范式,大概率会蔓延到其他垂直 FM——遥感、显微、声学、雷达

📐 跟今天下午的 WBench (video world model) 这条线,做的是同一类工作:某个 vertical 长出来的 FM 越多,representation-level benchmark 就越值钱

🧠 「embedding 到底学到了什么」这个问题,过去一年 LLM 圈也在重新认真问 (mechanistic interpretability)——计算病理这次是用 SDI 这套医学任务把它具体化了

🔬 论文 + SpaPath-benchboard 演示 + 19 个 PFM 完整名单 · 👇 评论区取

关注 @svtransit1 · 写给真在用 AI 的人

#AI #病理AI #FoundationModel #医学影像 #arxiv #硅谷中转站
