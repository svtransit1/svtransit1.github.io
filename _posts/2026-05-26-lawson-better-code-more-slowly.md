---
layout: post
title: "很多人现在用 AI 写代码,第一反应都是「我可以 ship 得更快了」。Nolan Lawson 这周一篇博客把整个故事翻过来——他用 AI,但用得更慢。"
date: 2026-05-26 12:25:31 +0800
source: https://nolanlawson.com/2026/05/25/using-ai-to-write-better-code-more-slowly/
hero: /assets/lawson-better-code-more-slowly/2026-05-26_1200_lawson-better-code-more-slowly-hero-1.png
topic_tags: [claude-code, codex, cursor, pr-review, ai-coding-craft, lawson, multi-agent-review, grill-me]
---

Lawson 是前 Mozilla 和 Microsoft 的 web 工程师,长年在开源圈维护项目,工程品味偏老派——意思是他会先问代码十年后还活不活,才问下周能不能 ship。

#多模型同时审一个PR

他这套方法的中心动作是:把同一个 PR 同时丢给 Claude sub-agent、Codex 和 Cursor Bugbot,让三个 agent 各自挑 bug、按严重程度(critical / high / medium / low)排序,然后他自己对照三家的结果做汇总。

Lawson 的原话——「扔越多不同的模型进 PR review,幻觉越少。」不是因为某一个 agent 特别厉害,是因为同一行代码三家都觉得有问题,大概率真的有问题;只有一家挑出来的,大概率是误报。

#修critical放过low

汇总完之后,他不是按列表从上到下全修。critical 和 high 让 agent 迭代修到干净,medium 和 low 直接放过——「修起来的工夫超过修了的价值」。

中间还会有一类 issue:agent 顺手发现的、不在这个 PR 范围里的老 bug。Lawson 也会去看一眼——但只看,不修。修不修,看那个 bug 在系统里的位置值不值得开新 PR。

#被审完之后还要被grill一次

修完 bug 不是终点。Lawson 接下来把 Matt Pocock 写的 /grill-me skill 调出来——这个 skill 的作用是,让一个 agent 反过来质问你刚刚的实现,把你逼到角落去解释每一个设计决定:「这里为什么这样写?」「这个边界你考虑了吗?」「这个 case 你 fall-back 到哪里?」

这一步看起来多余,实际上是整个流程里他最看重的一步——因为这是「你被迫去理解自己代码」的环节。多数 PR 在 LLM 加速 ship 模式下,作者自己其实没真的读懂改了的东西;/grill-me 把这个洞补上。

#慢的悖论

这一套全跑下来,一个 PR 的总时间不会比手写更短——但 Lawson 觉得它跑出来的代码质量、对 codebase 的理解、补进去的单元测试,都比之前「AI 加速 ship」模式下高得多。

他整篇文章的主旨,用中文一句话讲完就是:AI 让你 ship 得更快,所以你该 ship 得更慢。省下来的时间不是用来多塞 5 个 PR 进 review,是用来给同一个 PR 补单元测试、用 Mermaid 画一张这次改动到底动了哪几条数据流的图、把 agent 没看见的架构边界写进 markdown 文档。

他甚至承认这种用法很烧 token——「你可能烧掉一堆 token,最后发现整个方案根本是错的。」但他说这种 token 不算白烧,因为 agent 烧出来的失败,等于强迫他自己去想清楚架构本来该长什么样。这种「失败也算价值」的态度,跟过去十年「ship first, fix later」的 startup 文化是反向的。

#从加速器到放大镜

这篇博客现在在 HackerNews 首页第一,251 分,只发了 4 个小时——比绝大多数「AI 工具开箱」帖子都热,因为它戳到了每个真正写过几年代码的人心里都有的一种不舒服:LLM 让一切变快了,但「快」本身不是工程品味。

Lawson 不是在反对 AI 写代码,他用 Claude sub-agent、Codex、Cursor、Matt Pocock 的 /grill-me skill 用得比谁都熟。他只是把「用 AI」这件事从「加速器」重新定义成「放大镜」——放大你本来想做、但没耐心做的那些工程动作:多检查一次、多写一组测试、多看一眼 codebase。

未来一年,真正能拿住的 codebase,大概率不是 AI ship 出来最快的那批,是用 AI 慢慢 ship 出来的那批。

转给那个一直在「AI 加速 ship」模式里跑的同事——他可能会想换一种用法。

原文 + 工具清单 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #Codex #Cursor #PRReview #硅谷中转站
