---
layout: post
title: "【原来......很多人都不知道 Salesforce 有开源 AI-native 替代品?】🧱⚡"
date: 2026-05-28 12:00:00 +0800
hero: /assets/twenty-open-source-ai-native-crm/2026-05-28_1500_twenty-open-source-ai-native-crm-hero-6-raw.png
---

大部分 CRM 还停留在「人填字段」时代: 你登进去手动建联系人、改阶段、写备注, AI 顶多就是一个右下角的 chatbot 浮窗。Twenty 这个开源项目把这件事整个翻过来 — AI agent 和 chat 是 CRM 的核心。

GitHub 上 47,500 star, v2.8.0 两天前刚发布, 完整 TypeScript 全栈 (React + NestJS + Postgres), 可以一键自托管。

它实际能帮你做什么:

① 销售视角

- AI agent 自动做联系人 enrichment, 不用你一个一个查

- chat-first 操作: 在对话框说「把这个 deal 推到 negotiation, 提醒下周二」, agent 直接执行

- 自动化跟进: 失联超过 7 天的客户, AI 起草个性化跟进邮件

- 数据视图按需切换 (list / kanban / pipeline)

② 技术团队视角

- CRM 对象和字段用代码定义, 走 Git PR

- schema 改动可以 diff / 回滚 / code review

- 整个 CRM 配置打包成 app 发布, 团队间复用

- `npx create-twenty-app` 起步, Twenty SDK 写自定义对象

⚙ 5 步上手:

1 · Cloud 一分钟开通 (twenty.com signup), 或本地 Docker Compose 自托管

2 · 装 CLI: `npx create-twenty-app my-app`

3 · 用 Twenty SDK 定义你的自定义对象和字段

4 · `npx twenty app:publish --private` 发布到自己的 workspace

5 · 在 chat 里调用 AI agent, 让它自动跑工作流

Twenty 提的核心抽象叫「CRM as Code」: CRM 配置写成代码, 像软件项目一样可以 build / ship / version, 用 PR 改 schema, 用 git 回滚错误。

你可以建的两个典型 Workflow:

— 销售 Workflow · 「线索清理 + 自动跟进」

固定检查重复联系人、补缺字段、按互动时长分级、自动生成跟进邮件草稿、统计每周转化。

— 技术团队 Workflow · 「内部工具 CRM」

把 CRM 当作内部数据中枢, 定义你们 product 特有的对象 (用户/账户/合约), AI agent 跑常规审计 + 提示异常。

这件事的份量在工作流方式的转变 — AI 从 CRM 旁边的小弹窗, 升级成 CRM 的操作层。「又一个 Salesforce 替代品」只是表面, 下一年企业软件这条赛道, 这种 AI-native 重构会越来越多。

P.S. 自托管走 Docker Compose, 完整文档在 GitHub README; 47.5k star + 6.7k fork + 73 release 数据可查; 全栈代码 TypeScript, 协议看 repo。

转给那个一直被 Salesforce 折磨的销售或 ops 朋友 👇

关注 @svtransit1 · 写给真在用 AI 的人

🧱 Twenty GitHub repo + 官网 + Docker Compose 部署文档 · 评论区取 ↓

#Twenty #开源CRM #AIagent #自托管 #Salesforce替代
