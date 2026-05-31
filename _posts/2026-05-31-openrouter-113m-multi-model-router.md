---
layout: post
title: "「我做 AI 应用,到底该直接接某一家的 API,还是用 OpenRouter 那种一个接口接几百个模型的路由?」🤔 这两天这个问题有了个挺响的注脚:OpenRouter 刚融了 1.13 亿美元 B 轮。"
date: 2026-05-31 09:16:38 +0800
source: https://openrouter.ai/announcements/series-b
hero: /assets/openrouter-113m-multi-model-router/2026-05-31_0900_openrouter-113m-multi-model-router-hero.png
topic_tags: [openrouter, ai-infra, model-router, multi-model, funding]
---

先说它是干嘛的。OpenRouter 就是个「中间层」:你的代码只对接它一个 API,它在背后帮你接到 400 多个模型——OpenAI、Claude、Gemini、一堆开源的全在里面。想换模型、想按价格或速度自动选,基本不用改代码。而且它接的不只是文本模型——图像、语音、转写、embedding、视频模型也都在同一个接口里,做多模态应用时尤其省事。

为什么值得单独拎出来说?因为它公布的增长数有点猛:📈 每周处理的 token 量,半年里从 5 万亿涨到 25 万亿,翻了五倍;照这个势头,今年要处理超过一千万亿(quadrillion)个 token。背后是 800 多万开发者在用。

更说明问题的是这次的投资人名单:领投是 Google 旗下的 CapitalG,跟投里有 NVIDIA、Snowflake、Databricks、MongoDB……一线的云和数据基建几乎都来插了一脚。大家都想占住「模型路由」这一层——这本身就是个信号:多模型、而不是绑死一家,正在变成开发者上线 LLM 应用的默认姿势。

那回到你的问题。如果你只用一个模型、又把延迟和成本抠到极致,直连那一家可能更省心;但只要你想「多模型随时切换、按场景挑便宜的那个、出问题能立刻换备胎」,这种路由层能帮你省掉一大堆胶水代码和一堆 API key 的管理。它还带了花费管理、guardrails、零数据留存这些企业要的东西。

得说句实在的:这些使用数据全是 OpenRouter 自己公布的,营收和利润一个字没提——所以它证明的是「用的人多、长得快」,不等于「生意已经跑通」。🧐 但 1.13 亿加上这串投资人,至少说明这一层是真值钱。

转给那个还在把应用绑死在一家 API 上的同事。👇

关注 @svtransit1 · 写给真在用 AI 的人

🔗 OpenRouter 官方公告 · 第一条评论取 ↓

#AI #AI基建 #OpenRouter #LLM
