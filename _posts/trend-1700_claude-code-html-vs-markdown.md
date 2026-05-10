---
layout: post
title: "Anthropic 内部一个人发了条短文,主张 Claude Code 的输出最好用 HTML,不是 Markdown。HN 上 456 分、255 条评论,把社区直接吵成两边。"
date: trend 17:13:28 +0800
source: https://news.ycombinator.com/item?id=48071940
hero: /assets/1700_claude-code-html-vs-markdown/trend_2026-05-10_1700_claude-code-html-vs-markdown-hero-raw.png
topic_tags: [claude-code, html, markdown, anthropic, output-format]
---

发文的人是 trq212(Anthropic 员工)。他的观点很简单:让 LLM 生成 spec、dashboard、prototype、interactive doc 这类东西,与其吐 Markdown,不如直接吐一个 single-file 的 index.html——CSS + 一点 JS 就齐活。Markdown 看着干净,但能表达的东西太窄。

HN 上吵的不是观点,是代价。我看了一圈,意见集中在三条轴上。

**可视化丰富度**——HTML 赢。布局密度、配色、交互、动画,HTML 一把梭。Markdown 只能堆文字加引用块,做出来一个 dashboard 像 90 年代的论坛页。

**token 成本**——Markdown 赢,而且赢得很惨。HTML 多包标签层,带 inline style 更夸张,同样一份内容,从 Markdown 翻成 HTML 输出 token 量经常翻一两倍。HN 评论区有人直接把这条钉在原帖底下:作者在 Anthropic 上班,不自己付 token 钱,这条建议自带屁股。Cursor / Claude Code 这种按量计费的工作流,你用一星期就能从账单里看到差。

**人机共改**——Markdown 也赢。HTML 让人改起来麻烦,大段嵌套标签,reviewer 不愿意动。结果就是「让 AI 全包」的倾向更强,人退到后面去了。Markdown 是低门槛,HTML 是高墙。

我自己的取向:短期、一次性的 prototype 和 spec 演示,HTML 真的好用——尤其是要给非工程同事看的时候,interactive 元素能让 review 提速。但长期文档、需要多人接力的东西,Markdown 还是更稳——版本控制 friendly,diff 可读,没人愿意在 PR 里审 200 行嵌套 div。

Anthropic 内部的工作流可能整天都是「跑一次扔掉」的 artifact,他们写出这种偏好不奇怪——只是别忘了那是他们的语境,不是你的。HN 评论区另一个值得看的角度:Claude Code 给 web 开发者写 HTML 是天然主场,这条建议放到非 web 工程师身上(后端、ML、数据)就没那么顺,你最后还是得把那段 HTML 翻回纯文本归档。

最有意思的不是这场吵架本身。是 LLM 已经强到逼我们重新分清楚一件事:「给人看的格式」和「给模型生成的格式」,可能本来就该是两套东西。Markdown 当年赢就是因为它两边都还能凑合;现在两边的需求都拉开了,凑合的那个开始撑不住。

链接 · 👇 第一条评论

关注 @svtransit1 · 写给真在用 AI 的人

#Claude #ClaudeCode #AI #LLM #AI日报
