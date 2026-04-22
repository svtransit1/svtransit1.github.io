---
layout: post
title: "Mozilla 刚开源了一个 AI 客户端——五件事值得看。"
date: 2026-04-22 10:14:15 +0800
source: https://github.com/thunderbird/thunderbolt
hero: /assets/thunderbolt/2026-04-22_1005_thunderbolt-hero.png
topic_tags: [mozilla, ai-client, open-source, self-host, thunderbird]
---

项目叫 Thunderbolt，GitHub 刚过 3.5K 星，做这件事的人是 Thunderbird 邮件客户端那支团队。定位很直接：把「选哪个模型、数据存哪、账单交给谁」这三件事交还给用户。

1 · 背后的团队

不是新成立的创业小队，是 Thunderbird——那个做了二十多年开源邮件客户端、扛过 Firefox 生态最硬的一段路的团队。企业生产就绪、全盘加密、安全审计这些词写进路线图时，是有分量的。

2 · 模型后端：任你选

任何 OpenAI 兼容的 provider 都能接。挂 Ollama 跑本地 70B 可以，连 llama.cpp 的量化版可以，直接调 OpenAI / Anthropic 的云端 API 也可以。Thunderbolt 只做前端，模型你自己选。

3 · 平台覆盖

Web、iOS、Android、Mac、Linux、Windows 全都有。桌面三大系统都有二进制；移动两端齐了；Web 版直接打开就用。

4 · 自托管路径

想要自己的服务器：Docker Compose 一键起；再进一步，Kubernetes 的 Helm chart 部署。企业场景能走，独立开发者也能在 NAS 上跑。

5 · 在 2026 的定位

「前端客户端 + 中间网关 + 后端模型」这三层正在各自裂变。昨天聊的 GoModel 是中间网关的 Go 替代，Thunderbolt 就是前端客户端的开源答案。合起来就是一条完整的「不被任何一家 AI 公司绑死」的自托管链路。

6 · 数据在哪，主权就在哪

对话历史、上下文缓存、知识库附件——这些在官方客户端里都存在厂商的服务器上。Thunderbolt 的模式是默认本地，账户、聊天记录、自定义配置都落在你自己的机器或你自己租的 VPS 上。这个差别短期内看不明显，但在三年视角上，它决定了「你的 AI 历史」能不能带走。

MPL-2.0 开源，改过的代码开源回去。项目还在早期——跟 Claude.ai / ChatGPT 官方版比，团队协作、OAuth、插件生态都还差一截。但值得现在就装一个 Docker Compose 在本地跑着玩，感受「自己的 AI 客户端」大概是什么样子。

仓库：github.com/thunderbird/thunderbolt

转给那个每次订阅 ChatGPT / Claude 时都肉疼的朋友——他们可能更需要这个。

关注 @svtransit1 · 每天都有有用的 AI 资讯

#AI #Mozilla #开源 #AI工具 #Thunderbird
