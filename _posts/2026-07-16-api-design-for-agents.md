---
layout: post
title: "🧩 你把 API 设计得特别\"人性化\":默认值贴心、报错温柔、字段名简洁。结果接上 agent,它反而频频翻车。Freestyle 的创始人 Ben Swerdlow 最近点破了原因——给 agent 设计 API,和给人设计,几乎是两套相反的规矩。我们伺候人类开发者二十年攒下的那些\"体贴\",放到 agent 面前,大多成了坑。"
date: 2026-07-16 09:18:09 +0800
source: https://www.freestyle.sh/blog/opinion/designing-apis-for-agents
hero: /assets/api-design-for-agents/2026-07-16_0900_api-design-for-agents-hero.png
topic_tags: [api-design, ai-agents, developer-experience, mcp, tooling]
---

先说默认值。对人,默认值是贴心:懒得填的地方,系统替你兜底,少写几行是几行。agent 正相反,它会把整份文档一口气读完,每个参数该填什么心里门儿清。这时候默认值反而把它需要看见的信息藏了起来——它宁可自己一个个显式填,也不愿去猜你默认了什么、那个默认值配不配眼下这个场景。你省掉的那点输入,换来的是 agent 的不确定。

🚨 报错更明显。对人,报错讲究"别吓人、给个台阶下";对 agent,报错恰恰是它摸到正确路径最重要的线索。一条精确、指名道姓的错误——缺了哪个字段、该是什么格式、哪个值超了范围——能让 agent 当场自我纠正,一次就修对;一条含糊的"出错了,请稍后再试",只会让它抓瞎,一路越试越偏,把上下文全烧在瞎猜上。

🏷️ 命名也一样。一个通用的 name 字段,人扫一眼就懂,agent 却容易犯迷糊、开始幻觉——它拿不准这个 name 到底指显示名、还是唯一标识、还是别的什么。换成 displayName、externalId、slug 这种一眼见义的名字,它填起来不打折扣,跨文件、跨调用也不容易张冠李戴。

还有一层 Ben 说得挺狠:在 agent 时代,你精心包的那层 SDK 和 CLI,可能都是多余的。agent 真正读的是 OpenAPI 加一份好文档——它一次能吞下整份 spec,你为人做的那些"顺手"封装,对它反倒是一层要绕开、要反推的抽象。他有句话我记住了:一个 API 真正的价值,是提供 agent 自己推不出来的那个事实;剩下的花活,都是包装。

顺着这个思路,我自己补一句(不是原文):如果你手上在做任何 agent 会来调用的东西——一个 API、一个内部工具、一个 MCP server——评判它好不好的标准,正在悄悄从"人用着顺不顺手",换成"机器读不读得清楚"。显式、精确、可读,才是这个时代对 agent 真正的"体贴"。🤖

你正在建的那个接口,到底是为最后一个人类用户设计的,还是为第一个 agent 调用者设计的?

转给正在给团队搭 API 或 MCP server 的那个人。

完整链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #AIagent #API设计 #ClaudeCode #MCP
