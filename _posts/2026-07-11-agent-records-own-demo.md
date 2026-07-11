---
layout: post
title: "你让 agent 写完一个功能,顺口加一句\"录个演示视频\",它真就自己录了一个出来——脚本是它自己排的。🎬"
date: 2026-07-11 09:15:00 +0800
source: https://simonwillison.net/2026/Jun/30/shot-scraper-video/
hero: /assets/agent-records-own-demo/2026-07-11_0900_agent-records-own-demo-hero.png
topic_tags: [claude-code, agent, playwright, shot-scraper, workflow]
---

事情出在 Simon Willison 的 shot-scraper 上。1.10 版加了个 video 命令:你给它一个 YAML 写的 storyboard,描述在网页上依次做哪些操作,它用 Playwright 跑一遍,录成 mp4。storyboard 能写的动作也就那几样——open 打开页面、click 点某个元素、fill 填输入框、wait_for 等某个东西加载出来、pause 停几秒。看着挺普通。

有意思的是接下来这步。Willison 没自己写那个 storyboard,他让 GPT-5.5 去 review 一个分支的改动,然后甩了句"用这个新命令,录一个演示新功能的视频"。GPT-5.5 就把整个 storyboard 的 YAML 自己写出来了——先打开哪个页面、点哪个按钮、往表格里粘什么数据、等哪一步跑完,全给你排明白。他录的是 Datasette 批量导 CSV 的演示,一条命令 shot-scraper video xxx.yml --mp4 就出片。📹

我觉得真正的信号在这儿。"证明这段代码能跑"这件事,以前是个纯手工活:你得自己去点、自己开录屏、自己剪一段能看的出来。现在它被折进了 agent 的工作流里——写完功能,顺手让它自己出一个演示。proof-of-work 不再是你回头补的东西,而是 agent 交付的一部分。🧐

当然别高估它。storyboard 是 agent 照页面结构猜的,交互一复杂,大概率得你回去补两笔;shot-scraper 也小众,不是每套栈都现成。但方向已经很清楚了。

下次 agent 帮你写完一个功能,别只让它跑测试——让它录个视频,放给你看看它到底做了啥。

转给那个还在手动录演示视频的朋友。

关注 @svtransit1 · 写给真在用 AI 的人

原文链接放在第一条评论 ↓

#AI #ClaudeCode #AIagent #AI工具
