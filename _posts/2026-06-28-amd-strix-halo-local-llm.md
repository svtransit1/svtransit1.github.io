---
layout: post
title: "「想在家跑大模型,又不想给 Nvidia 交『显存税』💸——AMD 现在到底能不能打?」"
date: 2026-06-28 21:21:35 +0800
source: https://github.com/kyuz0/amd-strix-halo-vllm-toolboxes
hero: /assets/amd-strix-halo-local-llm/2026-06-28_1850_amd-strix-halo-local-llm-hero.png
topic_tags: [local-llm, amd, strix-halo, vllm, rocm, unified-memory]
---

能,但很多人一上来就押错了宝。大家第一反应都是去抢一张大显存的 N 卡,可本地推理这条线上,真正卡脖子的从来不是显卡算力,是内存 🧠——模型装不进去,再猛的卡也白搭。AMD 新出的 APU「Strix Halo」(就是那颗 Ryzen AI MAX+ 395)走的正是统一内存的路子:CPU 和 GPU 共用一块内存,这本来是 Apple M 系列在本地推理上一直占的便宜,现在 x86 这边也算补上了。

具体怎么落地?GitHub 上有个叫 amd-strix-halo-vllm-toolboxes 的项目,把在 Strix Halo 上跑 vLLM 的整套环境塞进一个容器,一个脚本 refresh_toolbox.sh 拉起来就能用。玩过 AMD 跑模型的都懂 ROCm 有多劝退——版本对不上、编译报错、显卡不认,光把 vLLM 跑通就能耗掉一个周末;这个 toolbox 把这块硬骨头替你啃了。更狠的是,作者把两台机器用低延迟互联拼起来,开 TP=2 的张量并行,凑出一块 256GB「显存」的单卡 🧱——这个容量,够你在桌上塞下一个 122B 的大模型(Qwen、MiniMax 都在它的测试名单里)。

别太上头的地方也得说清楚 ⚠️:它是社区项目,不是 AMD 官方出品;底层用的是 ROCm 的 nightly 构建,属于尝鲜阶段,翻车了自己扛。还有个数字容易被误读——它的跑分是「多用户峰值吞吐」,一堆请求一起压时的总速度;你一个人单独发一句,实际体感会慢不少。最现实的是,你还得先有那块 AMD 硬件,这一步它替不了你。

但方向我信:以后本地能跑多大的模型,越来越是内存说了算,显卡反而退居其次。

转给那个一直想在家跑大模型、又嫌 N 卡贵的朋友。

链接 · 👇 第一条评论

关注 @svtransit1 · 写给真在用 AI 的人

#AI #本地大模型 #LocalLLM #AMD #vLLM
