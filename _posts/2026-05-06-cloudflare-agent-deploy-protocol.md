---
layout: post
title: "Cloudflare 让 agent 自己开账号、买域名、绑信用卡、部署应用 —— 不用人插手。和 Stripe 一起搞的新协议，今天上线，每个 provider 默认上限 100 美金/月。"
date: 2026-05-06 15:11:16 +0800
source: https://blog.cloudflare.com/agents-stripe-projects/
hero: /assets/cloudflare-agent-deploy-protocol/2026-05-06_1115_cloudflare-agent-deploy-protocol-hero.png
topic_tags: [cloudflare, stripe, agent, deploy, agent-economy]
---

agent 能把代码跑起来这件事，从"调 API"升级到了"自己开公司"。把它能做的几件事拆出来看，每一项都是产品形态的转折点。

1️⃣ Discovery：自动查"我能买什么"

agent 不再需要工程师告诉它"用 Cloudflare Workers"。它直接调 REST API 列服务目录，看哪些产品能买、配额多少、价格多少。这一步把"工程决策"从人迁到 agent。

2️⃣ Authorization：身份验证由 Stripe 代办

agent 不直接接触你的密码或者信用卡。Stripe 做身份证明，OAuth 流程跑现有账号，Cloudflare 收到的是带签名的"代理授权"。这种"中介托管身份"的模式以后会越来越常见 —— 因为让 agent 直接拿密码或者信用卡，等于给一个还在迭代的系统开整个保险柜。账号系统是下一个被重构的层：你给 agent 的不再是一对 username/password，而是一张"代理授权令牌"，可以随时撤销、有作用域、有过期时间，像现在的 OAuth scope 但更细粒度。

3️⃣ Payment：tokenized + 100 美金/月默认上限

支付走 Stripe tokenized，agent 拿不到原始卡号。每个 provider 默认 100 美金/月封顶 —— 这条是关键，把"agent 自己花钱"这件事的炸弹拆了。出了问题最多 100 美金，不会一夜之间 5 万美金 GPU 账单跑满。这种"信任分层"的设计是 agent 经济能跑起来的前提：默认低权限、按场景升级、出事可追溯。前两年 OpenAI Operator 让 agent 看屏幕填信用卡那种姿态，已经被这套 token + 上限机制取代。

4️⃣ 全链路 deploy：从注册到上线一键完成

具体能做的事：建 Cloudflare 账号、订阅 paid plan、注册域名、拿 API token、部署代码、配 DNS、绑 SSL 证书。整条 startup MVP 流程，agent 一句话从头跑到尾。之前一个工程师手动配 30 分钟的活，现在变成 agent 一次工具调用。一个真实的 use case：你跟 Claude 说"做一个能上线的 AI 笔记工具，绑个看着像样的域名"，它能自己注册 ainotes.fun、起 Workers、塞代码、上 SSL，半小时之后真的有一个能用的网站。这件事一年前是科幻，半年后是日常。

5️⃣ Stripe Atlas 通道 + 10 万美金 credits

新通过 Stripe Atlas 注册的初创，获得 10 万美金 Cloudflare credits。这是 Stripe 在打"agent-first startup"这条赛道的姿态 —— 注册公司 → 接 Stripe → 用 agent 直接拉一整套云端基建。从开公司到上线，目标是 30 分钟。10 万美金 credits 看上去 generous，背后的算盘很清楚：把"开公司"的入口抢下来，后面 SaaS 订阅、支付通道、infra 采购就跟着粘在 Stripe 这条管线上。这种"下游粘性 + agent 端入口"的组合下半年会被 AWS、Google Cloud、阿里云抄一遍。

更大的信号比这个具体功能重要。"agent 自己花钱开服务"这条赛道，前两天 Anthropic 拉 Blackstone 做企业 AI 服务、Browserbase 把浏览器栈打包成 SDK、今天 Cloudflare + Stripe 把 infra 采购协议化 —— 三件事一起看，agent 工具栈正在从"模型 + 工具"演化成"模型 + 工具 + 商业身份"。下半年会有更多 SaaS 产品上线"agent 友好定价"。

中文 AI 圈值得记一下三点：第一，国内云厂商（阿里云、腾讯云、华为云）下半年大概率跟进类似协议；第二，国内支付环节是难点 —— 银联、支付宝、微信支付都没有 Stripe 这种 agent-friendly tokenized 流程；第三，合规上"agent 代理花钱"的法律边界还没人定义清楚。

完整链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #Cloudflare #Stripe #agent #AI工具
