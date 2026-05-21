---
layout: post
title: "每周下载 1 亿次的 Axios 也能被植入木马。这张图把 5 个步骤画清楚了。"
date: 2026-05-19 22:47:23 +0800
source: https://www.facebook.com/share/17H8VGvbqX/ (Boss · Discord 2026-05-18 22:36 SGT — Traditional Chinese FB post by hk6429 page, citing Korean YouTuber jocoding)
hero: /assets/axios-npm-supply-chain-trojan-vibe-coded-tools/2026-05-19_0800_axios-npm-supply-chain-trojan-vibe-coded-tools-hero-raw.png
topic_tags: [supply-chain, npm, axios, sapphire-sleet, north-korea, vibe-coding, security, teampcp]
---

重点看一下:

· 攻击者从维护者的 npm 凭证下手,推了两个毒版本 —— 1.14.1 和 0.30.4。

· 加了一个"幽灵依赖" plain-crypto-js@4.2.1 进去,跑 postinstall hook,mac / Windows / Linux 全打。

· 拿走 cloud key、数据库密码、API token,顺便装个 RAT 留后门。

· 微软把它归到了 Sapphire Sleet —— 北韩国家级 actor —— 还原成 3 月连续 5 个开源项目被打的 TeamPCP 行动。

vibe-coded 的小工具不查依赖树,被殃及的概率不低。建议过一遍 npm audit 和 package-lock,顺手扫一下 plain-crypto-js。

来源 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#NPM #Axios #SupplyChain #供应链攻击 #vibecoding
