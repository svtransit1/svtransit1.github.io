---
layout: post
title: "今天 X 上一张图传得挺凶:有人说,中国的 AI 模型在 OpenRouter 上已经全面反超了美国。这话听着像情绪,但我去 OpenRouter 的排行榜上扒了一眼真实数据——还真不是吹的。"
date: trend 17:29:45 +0800
source: https://openrouter.ai/rankings
hero: /assets/1700_chinese-models-overtake-openrouter/trend_2026-06-08_1700_chinese-models-overtake-openrouter-hero.png
topic_tags: [openrouter, chinese-models, deepseek, open-weight, model-adoption]
---

先说 OpenRouter 是什么:它是目前最大的模型 API 聚合器,无数开发者通过它调用各家模型。所以它的用量榜,不是看谁 benchmark 高,而是看开发者真金白银在用谁。这比跑分实在。

那本周的榜单长啥样?按调用量排,前四名,全是中国模型:第一是 DeepSeek V4 Flash,单周烧掉 3.69T token、占了 19% 的份额;后面紧跟着腾讯 Hy3、MiniMax M3、小米的 MiMo,每个都是两三 T 的量级。美国这边,Claude 系列(Sonnet 4.6、Opus 4.7、4.8)还在前十里撑着场面;但更扎眼的是——GPT 和 Gemini,一个都没进前十。整个前十里,六个中国模型、三个 Claude、一个是 OpenRouter 自家的。

而且发推那人说得对,这是个「2026 才发生」的故事。再往前倒一年,这张榜上还是美国模型一家独大;短短半年多,排位整个翻了过来。变化快到,如果你不是天天盯着,可能根本没意识到手边在调的,已经悄悄换了一批。

为什么会这样?我的看法是,这不是「谁更聪明」的胜利,是「开放权重 + 便宜」的胜利。

你想想开发者搭东西时在意什么:能不能自己部署、价格压不压得下去、跑量的时候调用心不心疼。DeepSeek、Qwen、MiniMax 这批,大多是开放权重——你能下载、能自己托管、能随便微调,API 价格又往往只有闭源大模型的几分之一。当一个开源模型的能力已经够用,旁边还有个贵好几倍的闭源选项,大批量场景里,开发者会选哪个,几乎不用想。GPT 和 Gemini 不是不好,是又闭源又贵,在「跑量」这件事上天然吃亏。开发者用脚投票,投的是性价比和可控,不是国别。

对你这个真在用 AI 的人,这事的实际意义是:如果你还在默认「能力最强的就该是 GPT / Claude」,可以去 OpenRouter 上,拿同一个任务,把 DeepSeek V4 Flash 这类放进去跑一跑、比比价。也许你会发现,自己手里那笔 token 账单,本来可以省掉一大半。

不过有两点得说清楚,别被那张图带跑。一,OpenRouter 只是一个切面——走它的多是独立开发者和中小团队;真正的大厂,很多直接用 Azure、Bedrock 接 GPT 和 Claude,这部分用量根本不进这张榜。二,用量高不等于模型就更强,它更多反映「好上手、便宜、开放」。所以准确的说法是:在 OpenRouter 这个开发者市场,中国开放模型赢得了使用量,而不是「中国 AI 全面赢了」。

但即便加上这些前提,这事的信号也够清楚了:当模型能力拉到同一档,开放和便宜,正在真实地改变大家手里在跑的到底是谁——这一次,变化不是发生在跑分表上,而是发生在真实的账单和调用量里。

数据来源 + 原推 · 第一条评论 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #DeepSeek #开源模型 #OpenRouter #本地LLM
