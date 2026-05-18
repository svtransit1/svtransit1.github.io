---
layout: post
title: "闭源 Grok 订阅,从今天起可以在开源 Hermes Agent 里跑。这件事比表面看上去深 —— 是闭源 SaaS 第一次主动给开源 agent 装 USB 接口。"
date: 2026-05-17 00:19:30 +0800
source: https://x.ai/news/grok-hermes
hero: /assets/grok-hermes-closed-inside-open/2026-05-17_0010_grok-hermes-closed-inside-open-hero-raw.png
topic_tags: [grok, hermes, xai, nous-research, ai-agent, open-source]
---

xAI 这周公告(标题朴素:Connect Grok to Hermes Agent),把 SuperGrok 订阅打通到了 Nous Research 的 Hermes Agent 里。这家 Nous 不熟悉的话简单介绍一下 —— 开源 LLM 圈里 Hermes 系列的微调团队,前两年靠 Hermes-2-Pro 那一波打出了名气。这次 Hermes Agent 是他们做的"持久化、自我改进"agent 框架,GitHub 已经 15.3 万星。

具体可以做什么:

1 · 用 Grok 4.3 做文本对话和高级推理

agent 跑在你自己机器(任何 PC / sandbox / VPS),但底下调用的是 Grok 4.3。等于"本地控制 + 云端能力"的组合。

2 · 接 Grok TTS 做语音回复

agent 自己生成 audio。Hermes 支持 WhatsApp / Discord / Telegram / Signal,语音可以走那些通道吐出来。

3 · 接 Grok Imagine 让 agent 生图 / 视频

这是这次最值得注意的一条 —— agent 自动决定何时生成视觉内容,而不是"用户手动开图像 tab"。

4 · 所有订阅 tier 都能用

不是 SuperGrok 专属,基础订阅也能挂上 Hermes。这个定价决定不容易,等于 xAI 把 Grok 当成"被嵌入的 inference 后端",而不是非要把用户拉到 grok.com 自己网站。

5 · 安装就一行 bash

curl 一句 install.sh 下来,跑 hermes model 选 xAI Grok OAuth,浏览器登一下,hermes --tui 就开始。半小时落地。

这件事真正的意义不在 Grok 多了一个 feature。是 framing 的转变 —— 闭源 SaaS 模型公司过去两年都在拼"我的 chatbot 网站 / 我的 app",护城河是用户停留时间。Hermes 这种 agent 框架是反过来的:用户的"使用面"主权回到本地,模型供应商变成可替换的后端。xAI 主动认这一点,等于承认下一代用户界面不是 grok.com,是用户自己机器上跑的 agent。

公告末尾还加了一句:"More open-source agents and integrations are coming soon."

转给那个还在用 grok.com 网页版的朋友 —— 安装包一行,值得换 stack。

关注 @svtransit1 · 写给真在用 AI 的人

完整链接 · 评论区取 ↓

#AI #Grok #Hermes #OpenSource #AIagent
