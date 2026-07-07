---
layout: post
title: "AI 一本正经编出来的假网址,正在被人抢注成钓鱼站——就等你的 agent 撞上去。⚠️"
date: 2026-07-07 17:19:00 +0800
source: https://unit42.paloaltonetworks.com/phantom-squatting-hallucinated-web-domains/
hero: /assets/1700_phantom-squatting-hallucinated-domains/trend_2026-07-07_1700_phantom-squatting-hallucinated-domains-hero.png
topic_tags: [ai-security, hallucination, agents, supply-chain, phishing]
---

一张图看懂这条攻击链(重点我标了橙色):Palo Alto 的 Unit 42 让模型生成了 210 万个网址,其中 1.3 万个已确认是恶意的,还有大约 25 万个「幻觉域名」没人注册、随时能被抢走。

真正扎心的地方在「可预测」这三个字——同一个模型会反复幻觉出同一个看着很靠谱的域名。攻击者不用猜,蹲点抢注就行。真实案例里,有钓鱼站在那个域名被标记 23 天后完成注册,有安卓木马足足等了 51 天。

对你意味着什么?如果你的 coding agent 会自己去 fetch 文档、点开模型给的链接,那「幻觉」就从「答错一次」升级成了一个供应链攻击面。

老实说,这是安全厂商自家的研究(PANW 顺手推销了自己五个产品),0.61% 的绝对比例也不算高——但这个方向值得你盯着。

你,敢让 agent 直接点开它自己「猜」出来的链接吗?
