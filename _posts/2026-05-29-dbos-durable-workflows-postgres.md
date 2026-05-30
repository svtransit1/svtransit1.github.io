---
layout: post
title: "你的 agent 跑到第七步，进程崩了。然后呢？整个流程从头再来，前面六步白干。😮‍💨"
date: 2026-05-29 12:28:47 +0800
source: https://www.dbos.dev/blog/postgres-is-all-you-need-for-durable-execution
hero: /assets/dbos-durable-workflows-postgres/2026-05-29_1200_dbos-durable-workflows-postgres-hero-1.png
topic_tags: [durable-execution, postgres, workflow, agent-infra, dbos]
---

想象一条很常见的 agent 流程：第一步调外部 API 取数据，第二步写进数据库，第三步发一封确认邮件。要是机器在第二步之后挂了，重启之后该怎么办？从头再跑，外部 API 白调一次、邮件可能发两遍；不重跑，那一半的状态就烂在那里。这就是 durable execution（持久化执行）要解决的事：程序每跑完一步，就把这步的结果 checkpoint 进数据库；万一崩了，从上一个完成的 step 接着跑，而不是从零开始。

通常碰到这个需求，你会被引去上 Temporal、Airflow、AWS Step Functions 这类编排系统。但 DBOS 最近甩了篇文章，标题很冲——「Postgres is all you need for durable execution」。一个 Postgres 就够，别的都不用。

它的做法挺反直觉：干脆不要那个单独的 orchestrator 服务。app server 直接跟 Postgres 对话。客户端提交一个 workflow，本质就是往 Postgres 的 workflows 表里插一行；各个 app server 轮询这张表，把活抢下来执行。整套调度逻辑，就压在一张表加几个 app server 上。🗄️

抢活靠的是数据库行锁。多台 worker 同时盯着那张表，用 locking clause 保证一个 workflow 只会被一台 worker 抢到，不会两台撞车。每跑完一步，worker 就把这步的输出 checkpoint 回 Postgres。这一步是关键：有了每一步的结果落库，重试就能做到「该跑的只跑一次」——万一真有两台 worker 抢了同一个活，数据库的唯一约束会在 checkpoint 那一刻发现重复，让其中一台直接退避。前面那条邮件流程里最怕的「发两遍」，就是被这层约束摁住的。

崩溃恢复也就顺理成章：某台 server 挂掉，它手上的 workflow 不会跟着陪葬——另一台 server 从 checkpoint 把它们捡起来，从上一个完成的 step 续跑。而且因为所有 workflow 的状态本来就躺在 Postgres 的表里，你想知道「哪些卡住了、卡在第几步、为什么失败」，直接写 SQL 查就行，不用再额外接一套监控。观测性几乎是白送的。📊

跟传统编排器最大的区别，就是这个「省掉中心节点」。Temporal 那套要单独养一个 orchestrator 服务，它既是可用性上的单点故障，也是一块额外要操心、要打补丁的攻击面。DBOS 的论点很直白：既然 checkpoint 这件事数据库本来就在做，那再单独立一个编排服务就没必要了，少一个组件就少一份运维和故障面。性能上，单台 Postgres 垂直扩一扩，能扛到每秒几万个 workflow——对绝大多数团队来说，这个天花板远在你够得着的范围之外。

还有一笔账容易被忽略：运维成本。Temporal 这类系统本身就是一套有状态的分布式服务，你得部署它、升级它、给它做备份、半夜还得起来救它。而 Postgres 是几乎每个团队本来就在跑、也最熟的那块基建——把 durable execution 塞进一个你已经养着的数据库，等于没多养一张嘴。这种「复用既有组件」的省心，往往比那点性能差异更值钱。💡

老实说，这类「X is all you need」的标题一半是营销话术。但 DBOS 这一刀戳得准：很多团队上 Temporal 多半是过度设计，真正需要的不过是 checkpoint 加重试，而这两件事 Postgres 本来就擅长，何必再背一套分布式编排的复杂度。当然，话不能说死——规模真到了变态级别、要跨多个数据中心做调度，专用编排器还是有它不可替代的位置。只是那条「该上 Temporal」的线，比大多数人以为的要远得多。在那之前，你手里那台 Postgres 大概率已经够用了。

所以问题留给你：你现在手上那个长任务、那条 agent 流程，崩了之后能从断点续跑吗？还是只能眼睁睁看它从头再来？

🐘 DBOS 原文：Postgres 搞定 durable execution · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #AIagent #Postgres #后端架构
