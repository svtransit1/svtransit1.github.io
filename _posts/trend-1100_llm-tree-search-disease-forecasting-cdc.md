---
layout: post
title: "这件事比一篇普通 AI 论文重要——一组 Harvard + UMass 的研究者让 LLM 自动写传染病预报模型,跑 2025-2026 这个完整的呼吸道病毒季节,实时对照 CDC 的人工 curation hub ensemble——结果是 LLM 写的 ensemble 一直平起平坐,有时候还赢。"
date: trend 11:12:35 +0800
source: https://arxiv.org/abs/2605.16238
hero: /assets/1100_llm-tree-search-disease-forecasting-cdc/trend_2026-05-18_1100_llm-tree-search-disease-forecasting-cdc-hero.png
topic_tags: [llm, scientific-ml, disease-forecasting, harvard, cdc, autonomous-science]
---

这事的来龙去脉是这样:美国 CDC 维护着一个叫 FluSight / COVID-Hub / RSV-Forecast Hub 的预测平台,聚合一群学术机构、政府组、企业实验室人工 curate 的预测模型,几十个模型组成 ensemble,每周向公众发布 4 周 forecast。这套 hub 是公共卫生圈里 forecasting 的金标准——能进 hub 的模型都经过严格审核,模型作者大多是流行病学博士。

Harvard 的 Michael Brenner(应用数学教授)+ UMass 的 Nicholas Reich(CDC hub 的实际运维者之一)+ Sarah Martinson 团队这周挂了 arxiv,标题朴素:"Prospective multi-pathogen disease forecasting using autonomous LLM-guided tree search"。做法是这样:

让 LLM 用 tree search 方式,**自己生成、自己评估、自己优化**预测软件代码。每一轮 LLM 写一个候选模型(Python 代码,能跑),用真实历史数据 backtest,根据误差排序;给排名靠前的模型做"变种"——参数微调、思路替换、特征工程改动;再跑一轮。LLM 同时探索流行病学理论的多个方向——SEIR 模型、机器学习方法、Hawkes process、贝叶斯层级模型——通过 tree search 在解空间里搜。

关键是结果不是 paper-only。**他们让这个 system 在 2025-2026 这个真实呼吸道病毒季节实时运行**——不是 cherry-pick 历史数据回测,是 prospective(向前预测),每周和 CDC hub ensemble 对照。三种病(流感、COVID、RSV)上,LLM 自动生成的 ensemble"持续平起或超过 CDC gold-standard ensemble"。

我觉得这事的深层意义不在数字。是它指向一个我们一直回避的真相:**很多被认为需要博士级人工 curation 的科学预测领域,LLM 自动化是可行的**。不是 LLM 取代博士,是博士的"调参 + 选模型 + 集成 + 验证"这一段工作流可以交给 LLM。博士空出来的精力可以去做更上游的事——理论突破、数据采集、政策对接。

更深的潜台词:CDC 的 forecast hub 之所以是"金标准",一部分是因为人工审核+多方独立提交+集成。LLM 的 tree search 在某种意义上是**单一 system 内复刻了这个 ensemble 多样性**——一个 LLM agent 可以扮演多个流派的方法学家,在解空间里 horizontal-explore。

下一步可见:其他被博士-人工-curation 守住的预测领域(地震 / 极端天气 / 经济 / 选举 / 供应链中断)迟早会被这套 path 渗透。Brenner 实验室历史上做过流体湍流的 AI surrogate、turbulence closure、reaction-diffusion 系统——这次跨到流行病学是个明确信号:他们在测"自动化科学家"这条 path 能走多远。

实操层面也有立刻可用的角度。如果你做 forecasting startup、做 quant、做 risk management,这个 tree search + LLM autocoding 的循环是个工具论文,不是哲学论文——代码层面可以拆出来移植到任何"模型→评估→变种"的搜索任务。它把一个本来需要资深 quant / 流行病学家手工跑几个月的 pipeline,压成 LLM 几小时能跑完的循环。边际成本和迭代速度都是数量级压缩。

转给那个还在以为"forecasting 需要人工 curate"的朋友——这件事的范式转变已经开始了。

关注 @svtransit1 · 写给真在用 AI 的人

完整链接 · 评论区取 ↓

#AI #LLM #DiseaseForecasting #Harvard #ScientificML
