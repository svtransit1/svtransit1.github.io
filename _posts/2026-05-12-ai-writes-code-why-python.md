---
layout: post
title: "「如果 AI 帮你写代码，你为什么还选 Python？」——这是 HN 前两天冲到首页 394 分的一篇文章抛出的问题。作者的论点很直接：过去 Python 占便宜，是因为人类写代码慢，省时间比省 CPU 重要；但 AI 写代码这件事，正在把这个前提抽掉。"
date: 2026-05-12 12:00:00 +0800
hero: /assets/ai-writes-code-why-python/2026-05-12_1450_ai-writes-code-why-python-hero.png
topic_tags: [python, rust, go, ai-coding, language-choice, agents, microsoft, anthropic]
---

文章拿出来的不是空话，是六个最近发生的具体项目：

**1. 微软自己把 TypeScript 编译器用 Go 重写了。** TypeScript 7.0 beta 就是这版，号称 10 倍性能。微软不是不会写 JS，是觉得这一步值得。

**2. Anthropic 的 Nicholas Carlini 用 Rust 写了一个 C 编译器。** 10 万行代码，全程靠 Claude agent 干活，整个项目算下来花了约 2 万美金 API 成本——一个人 + 一个 agent 就完成了。

**3. Steve Klabnik 两周时间写了 Rue 这个 systems 语言。** 7 万行 Rust。两周。一个人。

**4. Andreas Kling 把 Ladybird 浏览器的 JS 引擎挪到了 Rust 上。** 2.5 万行，也是两周。这是浏览器引擎，不是一个 Demo。

**5. Armin Ronacher 把 MiniJinja 从 Rust 移植到 Go。** 实际操作时间 45 分钟，API 费用 60 美金。开源社区最新的"贡献单位"已经不再是 patch，是 port。

**6. Python 自己也在变。** 这个生态里 27% 的项目用 Rust 写的二进制扩展，一年后这个数字变成了 33%。也就是说，主流 Python 库里越来越多的核心逻辑，本来就不是 Python 写的——是 Rust 写完再 binding 过来的。Astral 那一套工具（ruff, uv, ty）和 Bun 之所以一上来就赢，是因为它们没装 Python 的包袱。

作者的结论也不绕：你下一个项目的默认选择，不必再是 Python。难学的语言现在 AI 比你熟；编译反馈快、类型系统强的语言（Rust、Go、Swift）反而成了 AI 写得最爽的语言——因为 agent 能从编译器报错里立刻学到东西，迭代闭环极短。

我觉得这篇真正狠的地方不是"Python 完了"——Python 不会完，数据科学和原型期还是它的主场。狠的是「人类写代码慢」这个前提被拿掉之后，过去三十年关于"编程语言生产力"的所有讨论都得重算一遍。如果 Rust 写一个项目从前要 6 个月，agent 帮你写要 2 周，那 Rust 的"难"还算成本吗？

转给那个还在嘲笑 Rust 编译器很啰嗦的朋友——下一个浏览器引擎，他真有可能错过。

关注 @svtransit1 · 写给真在用 AI 的人

原始出处 · 第一条评论拿

#AI #Rust #Python #AI编码
