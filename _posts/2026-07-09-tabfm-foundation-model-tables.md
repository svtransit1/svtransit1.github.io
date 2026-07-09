---
layout: post
title: "做表格数据的机器学习,十年没怎么变的那套老规矩,Google 上月底想用一个「不训练」的模型掀了。"
date: 2026-07-09 21:15:00 +0800
source: https://research.google/blog/introducing-tabfm-a-zero-shot-foundation-model-for-tabular-data/
hero: /assets/tabfm-foundation-model-tables/2026-07-09_1830_tabfm-foundation-model-tables-hero.png
topic_tags: [google, tabfm, tabular-ml, foundation-model, zero-shot, xgboost]
---

先说这套老规矩:碰上一张表(Excel、数据库那种),先上 XGBoost 或梯度提升,再手搓一堆特征,针对这个数据集单独训一个模型。几乎人人都这么干。

6 月 30 号 Google 放出的 TabFM,是个针对表格的「零样本基础模型」:你把整张表——训练行,加上要预测的行——当成一整段上下文一起喂进去,它一次前向、权重冻着,直接给你分类或回归结果。官方一句话挺到位:它的 .fit() 什么都不训,只是把上下文存下来。不用为你的数据集再训模型、再搓特征。

为什么值得盯?NLP 早就被「基础模型 + 拿来即用」改写了,而表格数据,一直是这波浪潮没真正淹到的最后一块大本营——恰恰又是企业里最常见、也最值钱的那种数据。TabFM 把「零样本、开箱即用」搬了过来,等于给「一个数据集训一个模型」这条老规矩,递了张头一回像样的挑战书。

先泼盆冷水:这思路不是它首创,TabPFN 早就干过,Google 这次主要是把规模和行列混合注意力做上去;它也不会在每张表上都赢过一个调好的 XGBoost,别急着喊「XGBoost 死了」。而且「零样本」靠的是把数据当上下文读,表一大就可能塞不下;它又是拿合成数据训出来的,真实世界那种脏乱的表才是真考验。想验证的自己上手——我没实测,以上照官方讲的。

转给那个天天在调 XGBoost 的朋友,让他来泼泼冷水或者试试水。

关注 @svtransit1 · 写给真在用 AI 的人

链接 · 👇 第一条评论

#AI #机器学习 #Google #基础模型
