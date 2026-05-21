---
layout: post
title: "$900 的 bounty,招来 253 条 AI 灌水评论。"
date: 2026-05-19 09:15:17 +0800
source: https://archestra.ai/blog/only-responsible-ai
hero: /assets/archestra-git-author-block-ai-bot-spam/2026-05-19_0000_archestra-git-author-block-ai-bot-spam-hero.png
topic_tags: [github, opensource, ai-agent-spam, git-internals, archestra, maintainer-pain, sapphire-sleet-adj]
---

Archestra.ai 是一个做 MCP 周边基础设施的初创,CTO Ildar Iskhakov 这周把他们怎么处理 GitHub repo 上的 AI agent 洪水写出来了。读完比较有体感的不是 git 技巧本身,是这件事到底有多日常。

发生了什么:他们挂了一个 $900 的悬赏,要做 MCP Apps support 这个功能。issue 下面到 253 条评论时,真实贡献者已经被淹没。原话是 "GitHub 通知变成一面噪音墙"。另一边 x.ai provider 的 issue 收到 27 个 PR,大部分都没跑过测试。团队里有一个人一周固定花半天清 "AI 垃圾"。

然后他们做了个反直觉的事。GitHub 的 "prior contributor" 状态有个细节 —— 只认 author,不认 committer。Git 这两个字段是分开的:author 是改动是谁写的,committer 是谁把它推上去的。日常 git commit 时这俩一样,所以大部分人不知道能拆开用。

具体做法是,新人想进 repo,先填一份 onboarding,带 CAPTCHA、带 ethical AI 规则。过审之后一个 GitHub Action 自动拿到新人的 GitHub user ID,把名字写进 EXTERNAL_CONTRIBUTORS.md,然后用这段命令推上去:

git commit --author="their-username <ID+their-username@users.noreply.github.com>"

效果是这个 commit 落到 main 分支上,author 字段是新人,committer 字段是 Archestra 的机器人账号。GitHub 看 author,把新人标成 "prior contributor",从此评论和 PR 不会再被默认折叠。

整个流程从填表、CAPTCHA、Action 跑完,到新人 whitelist,全自动。

我觉得 git 技巧只是表面。Iskhakov 收尾那句话才是真意思 —— "We value quality over quantity. We don't value metrics pumped by AI slop." 翻成中文大概是 "我们看重质量胜过数量,不在意被 AI slop 灌水撑大的指标"。

OSS repo 现在两件事在同时发生 —— 工具越来越易用,贡献门槛越来越低;AI agent 也越来越多,贡献质量越来越随机。维护者夹在中间,以前的 "open by default" 慢慢扛不住了。Archestra 选了一个挺务实的路径:不关 repo,但把 "你是不是真实人类 + 是不是有 AI 滥用意图" 这个验证收紧到 onboarding 这一步。

如果你在维护公开 repo,这套 git 操作可以直接抄,但是 onboarding 那一关得自己设计 —— 抄 Archestra 的 ethical AI rules 只是起点。

转给在维护 OSS / 公开 repo 的朋友 —— 他们今天就需要这套。

链接 · 👇 第一条评论

关注 @svtransit1 · 写给真在用 AI 的人

#OpenSource #GitHub #AIagent #AI工具 #维护者
