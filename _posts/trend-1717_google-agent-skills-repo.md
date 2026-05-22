---
layout: post
title: "Google 在 GitHub 上开了个官方仓库,名字就叫 google/skills。点进去是它自家产品的一整套 Agent Skills——BigQuery、Cloud Run、Firebase、GKE 的上手指南,连云架构 Well-Architected Framework 的六根支柱(安全、可靠、成本、运维、性能、可持续)都拆成了单独的 skill。一行 npx skills add google/skills,挑着装就行。"
date: trend 17:17:00 +0800
source: https://github.com/google/skills
hero: /assets/1717_google-agent-skills-repo/trend_2026-05-22_1700_google-agent-skills-repo-hero.png
topic_tags: [agent-skills, google, anthropic, standard, ai-agent]
---

但仓库里塞了什么,反而是次要的。真正该停下来看的,是它用的格式。

Agent Skills 这套东西,最早是 Anthropic 给 Claude 做的:一个 SKILL.md 文件配一个文件夹,模型用到的时候才把它读进来,是个公开的规范。Google 这次没有另起炉灶搞一套自己的「Gemini Skills」,而是直接照着 Anthropic 的格式,把自家产品的用法写成 skill 交了上去。

仓库目前一万出头的星,43 个 commit,最新一次提交就在 16 小时前——还在持续往里加。骨架一个多月前就搭好了,里面的 skill 是最近才陆续填进去的。

标准成型的样子,大概就是这样。没有哪家开发布会拍着胸脯喊「我们要定行业标准」;它更像是某天你回头一看,连对手都懒得再造一个轮子,干脆往你的格式里写东西。Agent Skills 还很新,但 Google 这一手,等于替它盖了个章。

下一个把自家产品写成 skill 的大厂,你猜会是谁?

原文链接放在第一条评论 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #Claude #AIagent #AI工具
