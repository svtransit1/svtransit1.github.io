---
layout: post
title: "\"我用 Claude Code 月费,为什么这周突然多扣了一笔 API 账单?\"
date: 2026-04-30 12:13:46 +0800
source: https://github.com/anthropics/claude-code/issues/53262
hero: /assets/claude-code-hermes-bug/2026-04-30_1200_claude-code-hermes-bug-hero.png
topic_tags: [claude-code, billing, bug, hermes-md, anthropic]
---

如果你最近发现 Claude Code 用着用着冒出"超额计费"提示,这条 GitHub issue 值得花 3 分钟看一下。anthropics/claude-code 仓库 Issue #53262 — Claude Code 在某些情况下,会把"应该走包月配额"的请求错误路由到"按 API 计费"通道。触发条件很具体,几乎所有人都没意识到。

短答案是:如果你的 git commit message 里包含字符串 HERMES.md(或者类似命名的 markdown 文件提及),Claude Code 当前版本的请求路由逻辑会误判这次请求为"使用了外部 reference 文件",从而触发 outside-plan 的 API 计费,而不是吃掉你的月度配额。这个 bug 影响所有付费 Pro / Max 用户,因为他们以为自己在"包月吃到饱",结果 commit 里随手提个文件名就被多扣几块钱。

为什么会这样:Claude Code 的某个版本里加了对 commit message 的 context 扫描功能,目的是让 agent 能理解最近的代码变动。但这套扫描逻辑的"路由分流"代码有个 edge case — 出现特定字符串(包括 HERMES.md)时,系统判定这是"外部上下文导入",触发额外计费。Anthropic 官方还在调查根因,issue 评论区已经有几十个用户晒出账单截图,从月费 $20 突然被扣 $30-$80 的都有。这种"看不见的多扣费"在订阅型 AI 工具里特别危险 — 你以为已经包月吃到饱,结果系统在某个你不知道的逻辑分支里,悄悄按 API 计价跑了几个小时的请求,等月底账单出来才发现。Cursor 之前也踩过类似的坑,只是触发条件不一样。这一代订阅工具内部的"plan vs API"边界判定,普遍是黑箱。

具体怎么补?四件事这周做完比每天检查账单值得。先去 console.anthropic.com 看 Usage 里的 "non-plan API consumption" 那一行,如果有数字说明你被这个 bug 撞到了 — 开 ticket 引用 Issue #53262 申请处理,issue 状态已 closed,社区报告里已有用户拿到退款。临时修补可以做的是暂时不在 commit message 里写 HERMES.md 或者其他 *.md 文件名,需要引用就改成不带 .md 扩展(写"hermes notes"而不是"HERMES.md")。如果你跑生产工作流,可以暂时锁在出 bug 之前的 Claude Code 版本(具体版本号 issue 评论区有列),`claude-code --version` 看当前版本,brew 或 npm 装的可以指定旧版本号回退。最后给 GitHub issue 设个 watch,Anthropic 已经响应,大概率几天内出 hotfix,推送就升级。

我自己的判断:这件事说明 AI coding 工具的"包月 vs 按量"边界还在很模糊的状态。Claude Code、Cursor、Copilot 这一代订阅工具,内部用某种黑箱逻辑分流"plan 配额"跟"额外计费",用户根本看不到分流规则。下次出 bug 你可能还是被多扣一笔才知道。长期解法只能是 Anthropic / 厂商主动开放计费 API、明确分流规则,让用户能 audit 自己的额度消耗。

短期内,记得每周检查一次 console 里的 non-plan API consumption。这件事不需要恐慌,但 5 分钟扫一眼账单比写两篇技术文章对你长期更值。中文圈做生产项目用 Claude Code 的人尤其要警惕 — 国内信用卡处理跨币种额外扣费,退款流程比直接订阅麻烦得多,提前发现比事后追讨省事一个量级。这次 bug 是个 reminder:订阅型 AI 工具不是真的"全包",内部还有一层你看不见的计费分流,养成定期 audit 的习惯。

转给那个最近觉得 Claude Code 账单奇怪的同事 ↓

源链接在评论区 👇

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #Anthropic #Bug #AI日报
