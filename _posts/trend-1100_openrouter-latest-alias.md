---
layout: post
title: "OpenRouter 悄悄上了一个 \"~latest\" model alias 系列——你写 `~anthropic/claude-opus-latest`,它自动给你路由到当前最新版本的 Opus,不用每次手动改版本号。同样的 alias 跑到 Sonnet、Haiku、GPT、GPT-mini、Gemini Pro、Gemini Flash、Kimi 全家——目前一共 8 个 `~latest` 已经上线。"
date: trend 11:15:44 +0800
source: https://openrouter.ai/docs/features/models
hero: /assets/1100_openrouter-latest-alias/trend_2026-05-04_1100_openrouter-latest-alias-hero.png
topic_tags: [openrouter, model-alias, multi-vendor, claude, openai, gemini, kimi, dev-workflow]
---

为什么这件事值得停一秒看清楚。过去几个月每个大模型都在小步迭代,Anthropic 一两周一个 Sonnet 小版本、OpenAI 时不时换 GPT-mini 的内部 checkpoint、Google 给 Gemini Flash 加新能力、Moonshot Kimi 上周才发了 K2.6——你的代码里如果硬编码模型 ID,每隔一阵就得手工换字符串、跑测试、确认行为没变。这种"维护税"在多模型项目里会被乘上提供商数量,迅速变成一个不大不小、又不能不做的负担。OpenRouter 这一招把"挑当前最新"这件事抽到平台层面,你写一次 `~latest`,后面平台帮你跟。代码不用动,模型自动跟着升级。对那些不想被供应商版本号绑死、又懒得每周写迁移脚本的团队来说,直接省一档维护成本——尤其多 provider 路由的产品线,这种 alias 设计是比"自己写 fallback 列表"更优雅的解法。

唯一要小心的:`~latest` 等于"行为可能在你不注意的时候变",对于已经在生产线上跑的关键路径,你大概率还是要钉死具体版本号,留 `~latest` 给开发环境跟低风险任务用。这是个工具,不是默认推荐。各家自己也有别名机制(Anthropic 走 `-latest` 后缀,OpenAI 用 gpt-4o 这类自动滚动名),但 OpenRouter 把这件事在多 provider 之间统一了——这一层抽象在 multi-vendor agent 框架里特别有用。

链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #OpenRouter #Claude #开发工具
