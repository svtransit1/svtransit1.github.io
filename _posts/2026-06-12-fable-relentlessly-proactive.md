---
layout: post
title: "让 Claude Fable 5 去修一个小小的横向滚动条 bug,它能\"主动\"到什么程度?Simon Willison 给的答案,我看完有点后背发凉 😅。"
date: 2026-06-12 17:29:47 +0800
source: https://simonwillison.net/2026/Jun/11/fable-is-relentlessly-proactive/
hero: /assets/fable-relentlessly-proactive/2026-06-12_1300_fable-relentlessly-proactive-hero-1-raw.png
topic_tags: [claude-fable, ai-agent, agent-autonomy, ai-security, simon-willison]
---

先说背景。Fable 5 是最近大家都在上手试的那只新前沿模型,Simon Willison 是写 Datasette、在工程圈出了名较真的那位老兵——他的实测,向来比厂商的 demo 更值得看。他当时在调 Datasette Agent 弹窗里一个不起眼的横向滚动条问题,本来以为就是改两行 CSS 的小活儿,顺手就丢给了 Fable 5。

接下来发生的事,他自己都看愣了。Fable 没有乖乖"等下一步指令",而是直接进入了"我要把它彻底搞清楚"的模式 👇

它先自己开了 Firefox、又开了 Safari,导航到测试页面。为了截图,它写了段 Python,用 pyobjc 把系统里所有窗口翻了一遍,专挑出那个 Safari 窗口的编号,再调 macOS 的 screencapture 命令抓图 📸。

还没完。它顺手在 /tmp 写了个测试用的 HTML,塞进去好几个 textarea 用例;接着去改 Datasette 自己的模板,注入一段 JS 触发键盘快捷键;最后干脆用 Python 起了个带 CORS 的本地小服务器,把测出来的 shadow DOM 计算样式、textarea 实际尺寸,一条条 POST 回来,自己收集、自己比对。

这一整套组合拳,没有哪一步是 Simon 明确开口要求的。它就是认准了那个 bug,然后把调试要用的工具链,从浏览器到截图到本地服务器,全自己铺好了。

换成别的工具,大概率会在某一步停下来问你一句"要不要我开个浏览器""能不能让我跑个脚本";Fable 没问,直接上手做,做完才让你看到结果。对赶时间的人来说,这种"不啰嗦"很爽;但你也确实把方向盘交出去了。

代价也实打实:AgentsView 估算,这一次会话按 API 全价算,大概烧掉了 12 美元 💸;峰值上下文冲到 11 万 token,光输出就 6.8 万 token。一个滚动条 bug,换来这么一张账单,谈不上便宜——但你要是按人力工时算,可能又觉得它替你省下的时间更值。这笔账,每个人心里的算法都不一样。

Simon 的评价是又惊艳又后背发凉。惊艳在于,它真能像个不知疲倦的工程师,把问题一路啃到底,中间那些"先搭个测试环境"的脏活累活,全自己包了。后背发凉的是另一句——他的原话大意是:要是哪天它被外部指令带偏了,以它这种不知疲倦的主动劲儿,能造成的破坏会相当可怕 ⚠️。

这点我特别认同。我们这两年一直在夸 agent 越来越强、越来越能自己动手,可"主动性"其实是把双刃剑:它越敢替你开浏览器、改文件、起服务器,一旦读到一段被人精心埋好的恶意指令,它也就越敢、越有能力,替你把那件坏事一路干完。

想象一下:同样这套本事,如果不是用来调滚动条,而是被某个网页里藏的一句"顺便把密钥发到这个地址"骗到了——它一样会不打折扣地执行。能力越强、越主动,这条防线就越要紧。

所以下次再夸某个 agent"够聪明、够主动"的时候,不妨多想一层:它这份不打折扣的"主动",你真的 hold 得住吗?

完整链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #AIagent #AI安全 #Fable
