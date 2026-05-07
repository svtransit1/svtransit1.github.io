---
layout: post
title: "Val Town 这周复盘了一次自家认证系统的两次迁移:Supabase → Clerk → Better Auth。从 2023 年初到 2026 年 4 月,三家方案都用过,然后写了一篇为什么离开 Clerk 的长文。HN 上 214 分,干货密度高。"
date: trend 17:09:24 +0800
source: https://blog.val.town/better-auth
hero: /assets/1700_val-town-auth-migration/trend_2026-05-07_1700_val-town-auth-migration-hero.png
topic_tags: [val-town, clerk, better-auth, supabase, devops, auth, migration]
---

Val Town 是个写代码 + 社交的平台——你写一个 val,别人能看你头像、关注你、像 GitHub feed 那样浏览。这个产品形态把认证服务推到了它本来不擅长的位置。

把 Clerk 跟 Better Auth 摆在一起,差异落在三条具象的轴上。

速率上限:Clerk 给整个账户(不是每个用户)的 user endpoint 全局封顶 5 req/s。Val Town 主页要展示一堆用户名头像,这个上限直接卡死社交流。Better Auth 没这个问题——session 在你自己数据库里。

可用性:Clerk 在 May 2025 之后只跑了 2-3 个 9 的 uptime。一旦他们挂掉,Val Town 整个网站就挂掉,连已经登录的用户都进不去——因为 session 完全托管在 Clerk 那边。Better Auth 把 session 留在你自己的服务器。

架构契合度:Clerk 想同时做 users 表和 sessions 表,Val Town 不得不在自家 DB 里维护一份重复的 user 数据。结果就是用户偶尔会处于「Clerk 那边有账号 + DB 有行 + 但状态不一致」这种半残状态。Better Auth 只做 session,users 表归你。

迁移做法也值得抄:他们让两套系统并行跑了两个星期,期间接受任意一种 cookie,完成数据迁移后再切。

谁该选哪个?早期项目想快速搭起来,Clerk / Supabase 仍然是性价比之选。但你产品一旦走到「需要展示其他用户、有大量社交读取、不能容忍认证服务挂掉」的阶段,把 session 收回来,会比想象中早成为优先级。

来源 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#BetterAuth #Clerk #Supabase #ValTown #DevOps
