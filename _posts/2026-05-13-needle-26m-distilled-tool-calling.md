---
layout: post
title: "Cactus Compute 把 Gemini 3.1 拆了——只拿走\"工具调用\"那一块,做成一个 26M 参数的模型,刚刚开源了。"
date: 2026-05-13 12:00:00 +0800
hero: /assets/needle-26m-distilled-tool-calling/2026-05-13_1200_needle-26m-distilled-tool-calling-hero.png
---

仓库叫 Needle,九小时前挂上 HN。做的事极窄:把前沿模型里 function calling 这一项能力蒸馏出来,其余全扔。结果这个 26M 的玩意儿不会推理、不会写诗、你让它聊天它都聊不明白。但你给它一个工具列表和一个用户请求,它选哪个工具、传什么参数,做得比 FunctionGemma-270M(大十倍)和 Qwen-0.6B(大二十几倍)都准。换句话说,他们押了一个赌:工具调用根本不需要通用智能,它本质是一个查表加格式化的任务,可以单独拎出来做得很小很快。

架构是真的小。8 层 decoder,embedding 维度 512,8 个 attention head——这种规模放二十年前就是个研究 toy,放今天能装进任何手机、laptop、嵌入式板子。Cactus 自己的平台上跑出 prefill 6000 token/秒、decode 1200 token/秒,本地推理范围。换算一下,一个典型的工具调用决策——用户说一句话、模型读完工具说明书、输出一个 JSON——整轮在端上几十毫秒以内就走完了,完全感知不到延迟,而且不烧一分 API 钱。

对比一下现在的常规打法:同一个决策丢给 Opus 或 Gemini Pro,延迟轻松 1-3 秒,token 计费按千计,每多接一个工具说明书还要塞进 prompt 重读一遍。

这件事真正有意思的地方,不是又一个开源小模型,而是它把一个被严重低估的浪费点指出来了——现在大多数 agent 栈,从 LangChain 到 Claude Code 到那些"你的私人助理"类产品,工具路由全是丢给前沿大模型在做。Needle 押的方向是把这层分工剥离出来。前面用一个 26M 的本地小模型决定"调什么、传什么",后面再让大模型专心做实际工作。这是一个"Whisper for tool calling"式的拆解——能力从前沿模型里抽出一小块,体积砍到 26M,权重直接开放。

仓库还带了 playground UI,自己塞一组工具进去就能微调出领域专用版本——做家庭自动化的塞家电 API,做 coding agent 的塞 git/shell/file 工具集,做客服 bot 的塞 CRM API。这种"针对场景蒸馏一个 router"的玩法,以前要选 Claude Haiku 或者 Llama 3.3 8B 当中转还嫌慢嫌贵,现在 26M 就够了,推理在端上完成,API 钱完全不出。

下一波 agent 框架可能不再比"我们接入了哪些 LLM",而比"我们用哪个微模型做 dispatch"。Needle 不是终点,是个示范——你可以从 Gemini 那种庞然大物里抽走一项具体能力,做小、做开。后面会有专门做总结、专门做实体抽取、专门做意图分类的一系列 26M 微模型,组成 agent 栈的中间层。前沿大模型留给真正需要思考的事。

转给那个还在让 Opus 当 router 的朋友——给他省点 API 钱。

关注 @svtransit1 · 写给真在用 AI 的人

来源 · 评论区取 ↓

#AI #LocalLLM #AIagent #开源模型
