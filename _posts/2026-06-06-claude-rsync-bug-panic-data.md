---
layout: post
title: "「Claude 把 rsync 写崩了」——这条说法五月底传遍全网,差点把一个开源维护者逼到崩溃。后来真有人去把数据扒了一遍,结论有点出人意料。🧐"
date: 2026-06-06 C) — spa +0800
source: https://alexispurslane.github.io/rsync-analysis/
hero: /assets/claude-rsync-bug-panic-data/2026-06-06_1500_claude-rsync-bug-panic-data-hero.png
topic_tags: [claude, ai-coding, rsync, open-source, data-analysis, myth-check]
---

rsync 是几乎所有 Linux 系统都在用的文件同步工具。五月底,有人在它的 GitHub 仓库开了个 issue,标题措辞很冲,大意是「别用 AI 把这软件搞崩」,矛头直指项目里用了 Claude 辅助写的代码。三百多条评论,从认真讨论一路吵到人身攻击,维护者据说还收到了死亡威胁。可吵了半天,最基础的问题没人回答:Claude 到底有没有真的让 bug 变多?

一位独立分析者去算了一遍:rsync 三十六个版本、从 v2.4.6 到 v3.4.3,其中只有两个是 Claude 时期的。按「每十次提交、加权严重度的 bug 数」算,Claude 时期平均 1.65,而历史平均是 2.95——反而更少。置换检验 p 值 46%、Fisher 检验 74%,都说明这两个版本和历史没有统计意义上的差别。📊

⚠ 但先别急着拿它去赢吵架。这只是一个人的博客、没经过同行评审;Claude 时期只有两个版本,样本小到没法外推;连 bug 的严重度都是另一个大模型打的分。作者自己都把这些坑写在了前面。

也别立刻荡到反面——「这次没问题」不等于「AI 代码很安全」。今年另有研究发现,大模型生成的代码里约四分之一带着确认漏洞。所以真正该记住的是两条:别因为一个传得很响的说法就给人扣帽子、甚至骂人;同时,不管代码是 AI 还是人写的,该 review 的一行都不能少。

数据不会自动平息情绪,但至少能让你在开骂之前先停三秒。

转给那个还在转发「AI 把 XX 写崩了」的朋友。

原文链接放在第一条评论 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #Claude #AI编程 #开源 #AI日报
