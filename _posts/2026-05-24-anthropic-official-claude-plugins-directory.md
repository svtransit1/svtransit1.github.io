---
layout: post
title: "Anthropic 这两天悄悄上线了一件该有人做的事:Claude Code 的官方 plugin 目录,挂在 github.com/anthropics/claude-plugins-official——自己的 org 下,公司挂名,不是员工个人项目。已经 26.9K stars、684 个 open issues、2.9K forks。"
date: 2026-05-24 18:17:56 +0800
source: https://github.com/anthropics/claude-plugins-official
hero: /assets/anthropic-official-claude-plugins-directory/2026-05-24_1800_anthropic-official-claude-plugins-directory-hero-raw.png
topic_tags: [anthropic, claude-code, plugins, ecosystem, github, npm-registry-analog, plugin-marketplace]
---

结构分两层:`/plugins` 是 Anthropic 自己写、自己维护的插件;`/external_plugins` 是社区和合作伙伴贡献的,通过质量和安全审查、走 clau.de/plugin-directory-submission 这个表单提交。

装的命令也统一了:`/plugin install <名>@claude-plugins-official`,或在 Claude Code 里 `/plugin > Discover` 浏览。

为什么这事值得放下来想——

过去半年,Claude Code 的扩展生态像 npm registry 出现之前的 Node:好东西有,但散。每出一个新工具,你跟着 Twitter 上某个开发者的链接走;装个东西要自己 clone、读 README、希望没人投毒。Tesla skill(@ppressdev)、OpenCode 164K stars——都是这种「散点繁荣」。

Anthropic 自己出手做目录,等于签三个名:这些插件值得用、装法统一、出问题有 tracker。这就是 npm registry 之于 Node 的角色:把碎片化散点变成可索引、可信任、可规模化的层。

更大的信号在商业层:Anthropic 不只想做 frontier 模型,也想做对应的应用层基础设施。下一步大概率是付费插件、企业白名单、Anthropic 自己的「插件商店」抽成。

如果你在做 Claude Code 工作流,这个目录现在就值得收藏。如果你在做插件,提交表单值得走一遍——Anthropic 背书的目录位置,比自己发推被刷过去强很多。

转给那个还在到处 clone 第三方 Claude Code 工具的朋友——以后从这个目录开始找。

仓库 · 👇 第一条评论

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #Anthropic #Plugins #DevTools
