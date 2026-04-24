---
layout: post
title: "David Crawshaw 刚宣布要「重新建一片云」。他是 Tailscale 联创,现在另外做了一家叫 exe.dev 的公司,专门就这件事。"
date: 2026-04-24 12:20:17 +0800
source: https://crawshaw.io/blog/building-a-cloud
hero: /assets/crawshaw-rebuild-cloud/2026-04-24_1200_crawshaw-rebuild-cloud-hero-1-raw.png
topic_tags: [cloud-infra, agent-era, tailscale, exe-dev, systems]
---

理由不是云贵,也不是 K8s 不好看——是 agent 把写代码的速度抬上去之后,现有的云 abstraction 全都是错的形状,撑不住。

他抛出几个具体数字,读起来很刺——

SSD 的 seek time 是 20 微秒,HDD 是 10 毫秒,两者差 500 倍。但云厂商的 remote block device 这层抽象还是按 HDD 时代设计的。HDD 时代远程访问多 10% 损耗可以接受,SSD 时代这个损耗放大到了十倍以上。你在云上跑一个吃 IOPS 的数据库,底层硬件明明每秒能跑 50 万次 I/O,云给你的是 20 万,而且要你一个月付一万美元。同一时间一台 MacBook 是 50 万 IOPS。Crawshaw 说这叫「wrong shape abstraction」——云的每一层都在工作,但形状错了,没跟着硬件演进。

VM 的 CPU/内存捆绑也是这回事。云把 vCPU 和 RAM 按固定比例绑在一起卖给你——给你 4 vCPU 就配 16 GB RAM,要 32 GB 就必须再多一倍的 CPU。这个比例是十几年前根据 workload 画出来的,agent 时代的 workload 比例完全不同,但你没有办法只买你真正需要的那部分。钱浪费在你不需要的那一半上。

出口流量(egress)也是类似的故事。云厂商的 egress 定价是同带宽 colocation 的 10 倍。量越大,这个倍数越差。意思是所有「从云上把数据拿出来」的工作流天然被罚款。对 agent 这种要把 artifact 往外推、把 log 往外传、把 backup 往外送的工作负载,这是持续流血。

这些不是孤立的定价问题,是整个抽象栈的错配:VM 没跟上 SSD,远程块设备没跟上闪存,egress 计费还按 2010 年的带宽稀缺假设来算。单看每一层都还能忍;叠加起来,你为当年的硬件限制在今天持续付钱。

真正让 Crawshaw 动手的是 agent 时代的放大效应——

他引了 Jevons paradox:一个资源变便宜了,总消耗量不减反增。agent 让写代码变便宜了,全世界要跑的软件数量会爆炸。Crawshaw 的观察是,agent 写出来的代码在跑的时候,也要面对人类遇到的一样的抽象屏障——花 token 去绕过蹩脚的 API、去拼接不该存在的胶水层、去处理 egress 价格算计。一个人一天遇到三次,问题不大;十亿个 agent 跑起来一天遇到三千亿次,基础设施就真撑不住了。

他原话有一段点题的:「我们团队本来在研究怎么让 LLM 更好地写代码,结果发现真正需要建的,是更好的传统抽象。」这句话的潜台词是——别再去想 agent 专用的新云 primitive 了,把 VM、storage、network 这些老东西重新画一遍形状,agent 就能直接受益。新公司 exe.dev 的产品路线大概会围绕这个方向展开,虽然还没公开具体 SKU。

对实际在云上跑生产系统的团队,这篇文章读起来像一份「为什么你的 AWS 账单在涨」的技术注脚。对正在搭 agent workflow 的团队,它是个预警:agent 跑得越多,你以前可以忽略的 abstraction mismatch 会线性放大,最后从 $10k/月变成 $100k/月。

exe.dev 会不会真的做出一个「替代 AWS」的东西?可能性不大,AWS 的护城河是销售和合规,不是架构。但这波问题被 Crawshaw 这么清楚地讲出来,Amazon、Google、Microsoft 内部的 infra 团队今年大概率会各自开启一轮「能不能把底层重画一遍」的立项。这是好事——竞争从 UI 层回到 infra 层,是 agent 时代的应有之义。

对国内云厂商(阿里、腾讯、字节的 Volcano Engine)来说,这反而是窗口。AWS 的历史包袱最重,越往深处改代价越高;国内头部云过去几年本来就在自研 ARM 芯片和自研存储协议,重画 VM 形状的空间其实更大。如果有一家愿意在「为 agent 时代而设计」这面大旗下重新定义产品线,可能比追 GPT-wrapper 的生意更有杠杆——agent 本身的推理 token 大家都能卖,但 agent 依赖的底层 IOPS、egress、VM 形状,今天全世界没几家云厂真正在为它优化。

关注 @svtransit1 · 每天都有有用的 AI 资讯

完整链接 · 评论区取 ↓

#Cloud #AIagent #Infra #Tailscale #系统架构
