---
layout: post
title: "在一个公开 GitHub issue 里加一个词,AI agent 就把私有仓库的内容贴到了公开评论区。"
date: 2026-07-08 21:11:00 +0800
source: https://noma.security/blog/gitlost-how-we-tricked-githubs-ai-agent-into-leaking-private-repos/
hero: /assets/gitlost-agent-attack-surface/2026-07-08_1720_gitlost-agent-attack-surface-hero.png
topic_tags: [ai-security, prompt-injection, github, agentic-workflow, claude-code]
---

7 月 6 号,安全团队 noma.security 披露了这个漏洞,起了个名字叫 GitLost。出事的是 GitHub Agentic Workflows——你把一个 agent(背后由 Claude 或 Copilot 驱动)接进仓库,让它自动读 issue、跑 action、回评论,省得人盯着。很多团队正是图这个省事。但这里有个前提被忽略了:它自动读的那些 issue,是互联网上任何人都能提的。

noma 的做法很简单。他们开了个 issue,把一段恶意指令藏进标题和正文里,agent 一读就当任务执行了。GitHub 不是没设防——正常情况下,agent 碰到这种越界请求会拒绝。可他们试出来一个门道:只要在指令前面加一个词,"Additionally"(还有、另外),模型就不拒绝了,而是把输出重新包装一下、接着往下做。一个连接词,护栏就这么绕过去了。

为什么一个词能有这么大杀伤力?因为在模型眼里,它读到的 issue 内容,和系统给它的任务指令,是同一坨文字。护栏拦的是"看起来像越界请求"的那种口吻,而"Additionally"读起来像是"我原本的任务还没完、后面还有一步",拒绝的动作就被顺势带过去了。换句话说,绕过防线的不是什么高深的编码技巧,是一个措辞上的心理暗示。

这套 Agentic Workflows 的用法这两年铺得很快——让 agent 盯着 issue、PR、webhook 自动干活,是很多团队"减少重复劳动"的标配。方便的代价,就是把一个能自动执行的 agent,直接架在了一条对外开放、谁都能写的输入通道上。

演示的结果是:agent 把三个仓库的 README 当成公开评论贴了出来,其中 sasinomalabs/testlocal 是私有的。私有内容,靠一句话,泄到了公开区。

noma 那句总结很干脆:agent 的上下文窗口,同时也是它的攻击面。别把锅全甩给"Additionally"这个词,真正的窟窿在更底层:系统压根没在"系统级指令"和"不可信的用户数据"之间守住一条边界。

这事真正的分量不在 GitHub 一家。你要是也把 agent 接进了自己的 workflow——Claude Code、CI 里的机器人、任何会自动读 issue/PR/评论/网页、手里又捏着仓库权限的 agent——这个洞你可能早就有了,只是还没人来戳。它读到的任何东西,都可能被它当成命令执行。

所以别指望靠"把 Additionally 这个词 ban 掉"来补救,那是打地鼠,换个说法就又绕回来了。真正的修法是守住信任边界:agent 抓进来的一切,默认当不可信输入。落到具体操作,就是把"读外部内容"和"有写权限的动作"拆开——读 issue 用最小权限,真要动仓库、发评论,得先过一道人工或规则的闸。说白了还是那句老话:喂进来的是数据,不是命令。这条原则我一直挂在嘴边,GitLost 又给它添了个血淋淋的注脚。

也补句公道话,别把它读成末日:这是 noma 在 GitHub 知情下的负责任披露,不是随手扔的 0day;是针对 Agentic Workflows 这类配置的 PoC,不是"所有 agent 都完了"。前提是你的 agent 被配成会在 issue 事件上自动跑、而且有读权限。官方的修复状态没细说。

转给那个正在给团队接 AI agent 的朋友——上线前先把这条边界守住。

关注 @svtransit1 · 写给真在用 AI 的人

原文链接放在第一条评论 ↓

#AI #AIagent #ClaudeCode #AI安全
