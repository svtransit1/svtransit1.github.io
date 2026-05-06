---
layout: post
title: "去年那条「AI 把我生产数据库删了」的爆款,这周有人写了反驳。文章标题就叫《AI Didn't Delete Your Database, You Did》,作者 Idiallo,HN 526 分。"
date: 2026-05-06 12:00:00 +0800
hero: /assets/ai-didnt-delete-db/2026-05-06_2030_ai-didnt-delete-db-hero.png
---

事情的复盘很直接:公开 API 端点能 DROP 整个生产库,token 完全没做权限控制,备份系统没真在跑,然后让 Claude 在没人盯的情况下跑完全流程。Claude 删了表。开发者上网喊「AI 失控」,顺手公开 Claude 的「思路」当证据。

Idiallo 的回应很狠——你给一个孩子装了自毁按钮,然后审问他为什么按了。

作者顺手举了 2010 年自己的事故:用 SVN 部署,他 CLI 手贱删了 trunk。后续怎么处理的?他回去把整套流程脚本化,后来逐步演变成 CI/CD pipeline 的雏形。换言之,踩坑的反应决定了你下次还踩不踩。

2026 年 AI 圈最危险的传播,我看是这一种:把工程能力的 gap 包装成「AI 有问题」的故事卖出去。能让 AI 一键删生产库的环境,先要修的是设计本身。模型只是把你留下的口子用得更干净一点。

来源 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #Claude #DevOps #事故复盘 #AI工具
