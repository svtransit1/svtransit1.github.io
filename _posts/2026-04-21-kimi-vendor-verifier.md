---
layout: post
title: "你从 OpenRouter、Together 或 Fireworks 拉 Kimi K2.6 的 API，拿到的结果和 Moonshot 官方 API 有差距——不是错觉。"
date: 2026-04-21 18:17:14 +0800
source: https://www.kimi.com/blog/kimi-vendor-verifier
hero: /assets/kimi-vendor-verifier/2026-04-21_1815_kimi-vendor-verifier-hero.png
topic_tags: [kimi, open-source, inference, ai-infra]
---

Moonshot 自己排查了一轮，发现很多所谓的「模型拉跨」其实是 provider 做的手脚：decoding 参数被悄悄改掉、底层又加一轮量化省成本。用户看不到，只能把锅扣在模型头上。开源模型在这一层的信任是断的。

这件事的动机很朴素——量化省算力，算力省钱。一个 70B 的模型跑 INT4 成本只剩 FP8 的四分之一，中间差价就是利润。只要没人验，没人会主动说。所以「同样的开源模型，在不同 provider 上跑出不同答案」这条事实，长期被当成玄学。

为了把这件事摆上台面，他们开源了 Kimi Vendor Verifier（KVV），六道题专门压测 provider 的真实实现：

Pre-Verification 是最基础的一道：验 API 参数有没有被 provider 吃掉，temperature、top_p 是不是真的生效。OCRBench 五分钟跑个多模态烟雾测试，跑通了再往下。MMMU Pro 盯视觉预处理，看有没有在 resize 上偷工。AIME2025 跑超长输出——KV cache 有 bug，这里就会现形。K2VV ToolCall 测 tool-calling 触发一致性和 JSON 准确率，商用 agent 最容易翻车的一层。SWE-Bench 跑完整 agentic coding 场景，因为要 sandbox，这道闭源。

硬件门槛不低：两台 H20 8 GPU 服务器，一整套串行大概 15 小时。但对 provider 来说，这就是一张公开体检报告；对用户来说，是一个可以让第三方闭嘴的依据。

开源地址：github.com/MoonshotAI/Kimi-Vendor-Verifier

比起多一个 benchmark，这件事更像给开源模型生态补了一块缺——「你付的是官方模型的钱，拿到的是不是官方模型」从感觉题变成了可验证题。模型的作者亲手给第三方部署立规矩，这个姿态在开源圈不常见，但大概会是接下来几家头部开源模型都要学的动作。

关注 @svtransit1 · 每 3 小时一篇 AI 前线

#AI #Kimi #开源 #AIInfra #AI工具
