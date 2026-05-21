---
layout: post
title: "「OpenAI 的 AI 自己解开了一道 80 年没人解开的数学难题?」——这两天你大概刷到了这个说法。它不算错,但「解开难题」这四个字,恰恰把真正有意思的部分盖住了。"
date: trend 17:19:05 +0800
source: https://openai.com/index/model-disproves-discrete-geometry-conjecture/
hero: /assets/1719_openai-disproves-erdos-conjecture/trend_2026-05-21_1700_openai-disproves-erdos-conjecture-hero.png
topic_tags: [openai, erdos, unit-distance-problem, ai-math, reasoning-model]
---

准确说,OpenAI 一个内部模型做的事是:推翻了一个挂了 80 年的猜想。1946 年,Erdős 提出「平面单位距离问题」——平面上放 n 个点,最多能有多少对点之间的距离正好是 1。几十年来大家相信,类似方形网格的排法基本就是最优,Erdős 还为此押了一个上界猜想:这个最大值的增长,只比一条直线快一点点,那个「快一点点」的部分还会随着点数变多慢慢趋近于零。这个模型构造出了一整族反例,把增长率实打实抬到了一个固定更高的量级——也就是说,流传了 80 年的「网格最优」信念,被直接证伪了。普林斯顿的 Will Sawin 后来还把这个改进幅度精确到了 0.014。要注意:难题本身的精确答案其实还没算出来,被解决的,是这个具体的猜想。

真正值得说的有两点。一是干这件事的,是一个通用推理模型——没有为这道题做任何特训,没有外挂一套专搜证明策略的脚手架。OpenAI 拿一批 Erdős 问题去测它,它就直接交出了证明。二是它的解法:模型把一道初等的几何问题,接到了代数数论上,用到了 infinite class field towers 这种很深的工具。这种跨领域的连接,连数学家自己都说意外。证明已经由一组外部数学家核对过,还写了一篇配套论文;Fields 奖得主 Tim Gowers 把它称作「AI 数学的一个里程碑」。OpenAI 说,这是头一回,一个数学子领域里的核心开放问题,被 AI 自主解决。

所以下次再看到「AI 解决了数学难题」,值得多问一句:它是真的算出了答案,还是推翻了一个旧假设、撬开了一个新方向。这次是后者——而在数学里,后者往往更要紧:一个被证伪的旧信念,能让一整批数学家重新去看一片他们以为已经看清的地方。

链接 · 👇 第一条评论

关注 @svtransit1 · 写给真在用 AI 的人

#AI #OpenAI #AI数学 #推理模型
