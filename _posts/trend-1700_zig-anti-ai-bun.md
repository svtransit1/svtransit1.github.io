---
layout: post
title: "Zig 拒收 AI 写的代码,结果 Bun 把跑出来的 4 倍提速锁在自己 fork 里,不打算上游了。"
date: trend 17:14:54 +0800
source: https://simonwillison.net/2026/Apr/30/zig-anti-ai/
hero: /assets/1700_zig-anti-ai-bun/trend_2026-04-30_1700_zig-anti-ai-bun-hero.png
topic_tags: [zig, bun, ai-policy, open-source, contributor-poker]
---

Zig 维护者的立场很硬:LLM 生成的 PR 一律不收。理由不是怕 AI 写错代码,而是怕"贡献过程"被 AI 短路掉——他们把开源协作叫 contributor poker,你来贡献,我陪你看牌、陪你练手,练出来的才是社区。维护人花时间带新人,不是为了提交速度,是为了下一代维护人。生成器一介入,这套循环直接断掉。

问题来了。Bun 是基于 Zig 改的运行时,他们这边没这道禁令,AI 辅助跑得飞快,核心路径压出 4 倍提速。正常逻辑该回流给 Zig,大家一起受益。但维护者那条线挡在这里——AI-assisted 改的代码不收,Bun 也不打算硬塞,干脆留在自己 fork 里。

这就尴尬了。一边是开源治理的原则:维护人的判断权重大于生成器的产出量。另一边是工程现实:工具已经好用到让坚持原则的项目开始掉队。短期 Zig 这套立场不会松动,但长期 fork 之间的性能差只会一轮一轮越拉越大。等到下游用户开始追问"为什么主线慢这么多",压力就推到维护者面前了。

这一轮被重写的不是代码,是开源协作的形态本身——谁有资格往主线推、推上来的算谁的功劳、谁来背后续维护的责任。这场对决才刚开局。

链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #开源 #Zig
