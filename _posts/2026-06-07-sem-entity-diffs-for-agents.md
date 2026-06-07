---
layout: post
title: "「为什么 AI agent 一碰到大改动,就容易看错、改串?」"
date: 2026-06-07 09:19:05 +0800
source: https://ataraxy-labs.github.io/sem/
hero: /assets/sem-entity-diffs-for-agents/2026-06-07_0900_sem-entity-diffs-for-agents-hero.png
topic_tags: [sem, ai-agent, code-diff, coding-tools, git, dev-workflow]
---

这事很多人都遇到过:让 Claude Code、Cursor 改点东西,小修小补还行,一旦改动一大,它就开始张冠李戴。一个很容易被忽略的原因,藏在最底层——它读 diff 的方式,还停留在「按行」。

你想想 git 的 line-diff 长什么样:逐行的加加减减。这对人看还行,对模型有点坑。最典型的就是改名:你把一个函数重命名,git 往往显示成「删掉两百行、又加了两百行」。agent 一看,很可能以为你删了个旧函数、另写了个全新的;而「这其实只是改了个名」这条关键信息,反而被埋在一大坨噪音里。改动越大,糊脸越狠,看错的概率就越高,顺带还多烧一堆 token。

最近 HN 上冒出来个叫 Sem 的小工具,想从这层「原料」上解决问题:别按行,按「实体」来。

摆一起就清楚了。传统 line-diff 告诉模型的是「第 12 到 220 行变了」,重写还是挪动,模型得自己猜;Sem 的 entity-diff 直接给的是「函数 X 改名成了 Y」「方法 Z 改了三行」「新增了一个类 W」——单位是函数、类、方法,不是行。信号干净,模型不用猜。官方自己的测试里,把 Sem 的输出喂给 agent,比喂原始 line-diff,准确率高 2.3 倍。

举个具体的:你把 getUser 改名成 fetchUser、顺手挪了两行。line-diff 里这是一大片红红绿绿,模型得连蒙带猜;Sem 里就一行——getUser 改名成 fetchUser、动了 2 行,agent 一眼就懂,token 也省了一大截。一个大改动的 line-diff 动辄几千 token,实体级的摘要可能几百就够,常年挂着 agent 跑的人,这部分省下来不是小数。

你可能会问:这不就是 LSP 干的事吗?不太一样。LSP 是给编辑器做跳转、补全、报错的,服务的是人;Sem 是专门把「变化」整理成模型好读的格式,输出能直接塞进 prompt,服务的是模型。

它也不只是个 diff。一共六个命令:diff 带改名识别;blame 按函数追责、不是按行;impact 告诉你「改了这里,哪些地方会受影响」;log 能查单个函数的历史;entities 把一个文件里的函数、类、方法全列出来;还有个 context,专门给 AI 按 token 预算挑上下文。等于把「让模型读懂一份代码」做成了一整套工具。工程上也轻:26 种语言塞进一个二进制,一次 diff 大概 8 毫秒,装起来就 brew install sem-cli 加一句 sem setup,直接挂成 git 的默认 diff 工具。

照例泼盆冷水:那个 2.3 倍是作者自己跑的,方法没公开、第三方也没复现,看个方向就好;工具本身也很新——才几个小时的 Show HN,license 都没写清楚,适合「值得一试」,别现在就压生产线。

谁最该试一下?天天用 AI 改代码、尤其改大仓库的人——你大概早被那种「改个名,agent 以为你删了半个文件」的场面气过几回。

但它戳的点是真的:这两年大家都在卷模型多会写代码,可喂给模型的「原料」——diff、blame、context——还停在给人看的 line 级老格式。也许下一个该升级的,不是模型,是这一层。

转给那个还在让 AI agent 啃原始 line-diff 的同事。

原始出处 · 第一条评论拿 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #AIagent #编程工具 #AI日报
