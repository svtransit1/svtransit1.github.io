---
layout: post
title: "【原来接手烂项目,第一步不该是打开 main 函数】"
date: 2026-05-30 15:32:47 +0800
source: https://github.com/Lum1104/Understand-Anything
hero: /assets/understand-anything-codebase-graph/2026-05-30_1500_understand-anything-codebase-graph-hero-4-raw.png
topic_tags: [claude-code, codebase, knowledge-graph, onboarding]
---

接手别人甩下的项目,几万行代码、文档等于没有、作者早跑路了。大多数人第一天就干一件事:从 main 函数开始一行行硬啃,啃到天黑还没搞清楚一个登录到底走了几层。😮‍💨

GitHub 上这个叫 Understand-Anything 的项目,最近冲到了四万多 star。它的做法很具体:把整个 codebase 嚼成一张能点、能逛的知识图谱,直接挂在 Claude Code 里当插件用。⚡

它分两层干活:先用 tree-sitter 把代码结构静态扒一遍——谁调谁、模块怎么连;再让 LLM 补一层语义——这个函数在干嘛、属于哪个业务域。两层叠起来,生成一张力导向的图,你拿鼠标在上面逛,而不是在十几个文件之间反复横跳。

两个最容易上手的场景👇

🔍 进新组、读祖传代码——先看图,再顺着它排的「学习路线」按依赖顺序逛一遍,比对着 README 干发呆强多了。

🧩 评审别人的 PR——一条 /understand-diff 看这个改动会波及到哪些地方,心里有底再下结论。

🗺 摸排一条复杂链路——在 /understand-dashboard 里点开节点、顺着调用关系往下跳,比在 IDE 里 Ctrl 点着点着就迷路强。

⚙ 在 Claude Code 里装,就两行:

1️⃣ /plugin marketplace add Lum1104/Understand-Anything

2️⃣ /plugin install understand-anything

装完你有一串斜杠命令能用:/understand 建图、/understand-dashboard 在浏览器里逛图、/understand-chat 对着整个项目问问题、/understand-domain 把藏在代码里的业务流程抽出来。

真正的心法说穿了就一句话:「把'理解这个项目'这件事,缓存成一张能复用的图。」💡 你可能会问,直接让 Claude 自己读一遍不行吗?行,但每开一个新会话它就得重读,几万行全喂进去、token 哗哗烧还容易读串;这张图建一次、存下来、只增量更新改过的文件,后面每次问都省得从头来。

也别神化它——语义那层是 LLM 写的,会烧 token 也会看走眼,它给的是一张「大概长这样」的地图,真要动关键逻辑,该读的那几行还得自己一行行读。

P.S. 它不只啃代码——/understand-knowledge 还能拿来理一份 wiki 或一堆散文档,套路一样:先建图、再逛。它支持十几个 AI 工具(Cursor、Copilot…),输出能选中文,而且是增量的,改过的文件才重新扫。

说到底,以前「读懂一个项目」靠的是时间加老员工带;现在至少先有了一张能随时问的地图,新人爬坡那几天能省下不少。这事的重点从「谁记得这块代码」慢慢变成「图建得够不够全」。

转给那个还在硬啃祖传代码的同事,让他下次先 /understand 一下。🧐

关注 @svtransit1 · 写给真在用 AI 的人

原文链接放在第一条评论 ↓

#AI #ClaudeCode #AIagent #AI工具
