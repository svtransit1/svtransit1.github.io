---
layout: post
title: "\"Copilot 6 月开始按 token 收费,我要不要换工具?\"
date: 2026-04-28 19:31:00 +0800
source: https://github.blog/news-insights/company-news/github-copilot-is-moving-to-usage-based-billing/
hero: /assets/copilot-usage-billing/2026-04-28_1820_copilot-usage-billing-hero.png
topic_tags: [github-copilot, pricing, agentic, ai-economics]
---

GitHub 昨天宣布,从 2026 年 6 月 1 日起 Copilot 改用 "AI Credits" 计费 — Pro $10/月 含 $10 Credits,Pro+ $39/月 含 $39 Credits。token 用完了要么加钱要么等下个月。这是 AI 编码工具行业第一次有大厂明确承认:agent 模式下,扁平定价撑不住。

短答案:大部分人不用换,但要重新算账。代码补全和 Next Edit 永远免费,不吃 Credits。真正涨价的是 Copilot Workspace、Coding Agent 这种"读 N 个文件改一整个 feature"的长链条任务。

具体的量级感:Sonnet 4.6 跑一个普通 agent 任务(读 5 个文件、改 2 个 bug、跑测试)粗算烧 $0.15-$0.40 的 token。Pro 用户一个月 $10 Credits,理论上够 25 到 65 次小任务。但 workspace 那种"改一整个 feature"动辄 $1-$3 一次,Pro 做满 10 次就清零了。Pro+($39)能撑 100+ 次小任务或 30 次中等任务 — 这才是 GitHub 真正在拿捏的定价心理学,跟 ChatGPT Plus / Pro、Claude Pro / Max 完全一套思路:让重度用户感觉中档不够,自然往 Pro+ 升。

Credits 怎么扣也值得看清楚:input token、output token、cached token 都算,跟 Anthropic / OpenAI API 计费逻辑一致。所以一个长 context 的 agent 任务,光是把代码塞进去就先吃掉一截额度,再加上模型的思考输出和 tool call 来回,真实消耗比纯输出 token 高得多。

要不要换工具,看你具体怎么用。如果你主要靠补全 + 偶尔 agent,留着 Pro。如果 agent 是日常,要么升 Pro+,要么转向 Claude Code、Cursor Pro 限额、aider 这类按 API 直接计费的工具,自己算哪边划算。Business 用户头三个月有 $30 补贴、Enterprise $70,8 月以后才真金白银结账,IT 部门还有时间摸清团队真实用量。

GitHub 没有取消"补全免费"那一档,这点很关键。它在告诉用户:轻度用户继续白嫖,中度用户($10)按用量给额度,重度 agent 用户($39+)真金白银算。这种分层比 Cursor、Replit 那种"premium request 配额"透明多了 — 后者一个月给你 500 个 GPT-4 请求、20 个 Claude Opus 请求,让你自己分配。问题是用户根本算不清楚一次请求烧多少。token 计费虽然要算,但起码你能算出来。

更长远的信号是:这不是 GitHub 一家的事。Cursor、Replit、Windsurf 这些工具一直在用各种"premium request"配额绕这个问题,GitHub 这次直接掀桌子改成 token 计费,等于承认整个行业都要走这条路。下半年其他几家大概率会跟。"无限"定价在补全时代行得通,在 agent 时代是逼厂商砍模型、压上下文、玩各种限速把戏 — 改成显式计费,起码工具明面上能用满血模型跑长链条,只是钱要算清楚。

实操建议:如果你现在还在用 Copilot 当主力 agent 工具,这两周先打开 GitHub 账户的 usage dashboard,看看自己历史 agent 调用量,做个粗略 token 估算。6 月 1 日之前心里有数,要么主动升级,要么平滑切走。

中文圈独立开发者还要多想一步 — 国内信用卡付订阅本来就麻烦,Copilot 改成 Credits 之后,如果一个月烧超额还要补充值,操作复杂度更高。这点上 Claude Code 那种"绑定 Anthropic API 直接按 token 走"反而简单。规则透明一点,debug 自己工作流的成本结构反而更容易。

转给那个最近在算 Copilot 账单的同事 ↓

链接 · 👇 第一条评论

关注 @svtransit1 · 写给真在用 AI 的人

#AI #GitHubCopilot #AI编码 #AI工具 #AI日报
