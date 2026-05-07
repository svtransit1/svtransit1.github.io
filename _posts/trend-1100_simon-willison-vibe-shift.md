---
layout: post
title: "\"Simon Willison 是不是放弃 review AI 写的代码了?\"
date: trend 12:00:00 +0800
hero: /assets/1100_simon-willison-vibe-shift/trend_2026-05-07_1100_simon-willison-vibe-shift-hero.png
---

差不多是。Django 的共同创建者、写过几百篇 AI 评测的人,5 月 6 号在自己 blog 上发了一篇 442 分的反思——「Vibe Coding and Agentic Engineering Are Getting Closer Than I'd Like」。

他几个月前画过一条线:vibe coding 是给个人项目的——bug 只伤到自己,糊就糊了;agentic engineering 是给生产环境的——有经验的工程师用 AI 加速,但保持职业标准。这条线他自己之前坚持得很死。

现在线模糊了。他原文里写——「I'm not reviewing that code. And now I've got that feeling of guilt」。模型变可靠之后,他自己也开始把 Claude Code 当一个被信任的团队成员对待,而不是每行都要 review 的实习生。

"那他怎么决定哪些代码不 review?"

有一个具体阈值:任务足够标准化的时候。原文举的例子是「让 Claude Code 写一个 JSON API endpoint,接收参数、跑一段 SQL、返回 JSON」——这种东西它就是会写对。Willison 给这类任务加测试、加文档,跳过逐行 review,就跟在大公司里你不会去 review 每个同事的小 PR 是同一个逻辑。

他的结论也很硬:这事对就业冲击有限,真正发生的是瓶颈搬家。设计决策、需求验证这两件事,2026 年的权重显著高于「写代码的速度」。

我看下来感觉是这样:把代码 review 标准跨人和跨 agent 拉平,是 AI coding 进入下一阶段的标志。一年前你会觉得「不 review AI 代码」是不负责任的简称。现在,在标准化任务上,这反而是对工程师时间的一种合理分配。

来源 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#SimonWillison #ClaudeCode #AIcoding #VibeCoding #AI工具
