---
layout: post
title: "🧑‍💻 \"我让 Claude Code 写东西,十次有八次不是我要的;好不容易对了,代码又跑不起来——是不是我不适合用 AI 写代码?\"这个困惑挺多人有。TypeScript 圈的知名教育者 Matt Pocock 最近把自己的解法开源了:一套 Claude Code skills,思路很直接——AI 写代码好不好,拼的是工程纪律,模型强弱反而是其次。这套东西现在能直接装成 Claude Code 插件,也能配别的模型用。"
date: 2026-07-16 18:17:58 +0800
source: https://github.com/mattpocock/skills
hero: /assets/ai-coding-discipline-skills/2026-07-16_1800_ai-coding-discipline-skills-hero.png
topic_tags: [claude-code, ai-coding, engineering-discipline, tdd, agent-skills]
---

他先把"AI 写代码为什么翻车"拆成了四种毛病,每种配一招——招数你多半都认识,难的是把它们变成每次都会做的动作。

方向从一开始就偏了——agent 压根没搞懂你要什么。他的办法是先让 agent"反过来拷问你":动手之前,让它盘问你的计划,把你自己都没想清楚的地方一个个逼出来,对齐了再写。

没有共同语言——同一个东西你和 agent 叫法不一样,越写越歪。解法是先建一份 CONTEXT.md,把项目的"行话"、领域模型写清楚,让人和 agent 共用一套词。

代码就是错的——这个最直接,靠反馈闭环兜底:静态类型、测试、TDD,红-绿-重构一轮轮跑,不给它蒙混过关的机会。✅

架构烂掉了——写着写着成了一坨。靠的是"刻意设计":定期让 agent 扫一遍代码、指出该收拢重构的地方,主动还技术债,不等它自己烂穿。

这四招没一个是新词——拷问、领域建模、TDD、重构,全是资深工程师本来就在做的事。Matt 做的,是把这套纪律拆成一个个能重复调用的 skill,让"好好写"这件事不靠临场自觉,靠固定流程。

这四条毛病,天天盯着 AI 写代码的人多半条条眼熟。把 AI 写代码真正用出效果,靠的往往是把工程纪律焊进流程,模型多强反而是其次。🧭 你用 AI 写代码,是把它当自动补全,还是当一个需要你对齐、测试、复盘的初级工程师?

转给那个还在把 Claude Code 当自动补全用的同事。

原始出处 · 第一条评论拿

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #AI编程 #编程效率 #AIagent
