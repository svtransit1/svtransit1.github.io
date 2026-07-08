---
layout: post
title: "让 AI 去「操作」一个网页,你是不是还在开无头浏览器跑 Playwright,或者把截图丢给多模态大模型,让它「看」着页面再点?又重、又慢、还要一堆权限。"
date: 2026-07-08 12:16:00 +0800
source: https://github.com/alibaba/page-agent
hero: /assets/page-agent-in-page/2026-07-08_1200_page-agent-in-page-hero.png
topic_tags: [ai-agent, web-automation, dom, tooling, mcp]
---

阿里开源的 page-agent 把这事整个反了过来。你往网页里塞一个 script 标签,这个页面自己就长出一个 AI agent——直接读写 DOM、用文字指令操作,不截图、不上多模态模型、不装浏览器扩展、也不开无头浏览器。25k star、MIT 协议,一个 script 标签或者 npm 装上,一行 execute 命令就能跑;还带一个 beta 的 MCP server,能从外面调它。等于说,一行标签,任何网页就有了自己的手。

对你的意义:要是你想给自己的 SaaS 加一句「让 AI 帮用户点界面」,或者本来就在做网页 agent,这条路比架一整套浏览器自动化,轻太多了。

但先泼盆冷水:它的 README 全是功能介绍,一个准确率、一个 benchmark 数字都没有——到底靠不靠谱,没有数据背书;DOM 文字指令这套,在复杂、动态、canvas 很重的页面上历来不稳;不上多模态也意味着,纯靠视觉才认得出的元素,它根本看不见。方向很聪明,可「能跑」和「好用」中间还差得远,先拿不重要的页面试。

让 AI 操作网页,到底该从外面「看着点」,还是让网页自己长出手?page-agent 押的是后者。

转给那个还在用截图加 Playwright 硬撑网页 agent 的朋友。

链接 · 👇 第一条评论

关注 @svtransit1 · 写给真在用 AI 的人

#AI #AIagent #Web自动化 #AI工具
