---
layout: post
title: "NotebookLM 很好用,但有件事你可能没细想 🤔 你喂进去的那些 PDF、研究资料、内部文档,全都上传到 Google 了。有个开源项目专门解决这件事——Open Notebook,一个能自己部署、数据不出本机的 NotebookLM 替代品。这周刚发了 v1.9.0,GitHub 上 26.9k 星。"
date: 2026-06-07 21:16:07 +0800
source: https://github.com/lfnovo/open-notebook
hero: /assets/open-notebook-self-hosted-notebooklm/2026-06-07_2100_open-notebook-self-hosted-notebooklm-hero-raw.png
topic_tags: [open-notebook, notebooklm-alternative, self-hosted, local-llm, privacy]
---

先说它到底是什么。Open Notebook 把 NotebookLM 那套核心能力——把一堆资料丢进去,让 AI 帮你梳理、问答、甚至生成播客——原封不动搬到了你自己的机器上。区别就一个,但很关键:数据全程待在你这边,不经过任何云。

为什么这点重要?如果你处理的是公司内部文档、还没公开的研究,或者任何不想交给第三方的东西,「上传到 Google」这一步本身就是个坎。尤其在国内,数据合规和隐私这事越来越较真。Open Notebook 把这个坎直接抹掉了。

具体能干什么,值得展开说几句 👇 它支持 18 个以上的模型提供商——OpenAI、Anthropic、Google、Groq、DeepSeek、xAI 都有,更关键的是 Ollama 和 LM Studio 也在列。换句话说,你可以全程跑本地模型,一个 token 都不往外发。输入类型很全:PDF、视频、音频、网页、Office 文档都能喂进去。搜索是全文加向量两种一起上。它还带一套完整的 REST API,想接进自己的流程里也没问题。

播客这块它甚至比官方还狠 🎙️ Google 的 NotebookLM 生成播客是固定两个人对谈;Open Notebook 能配 1 到 4 个说话人,角色还能自己定。

怎么上手?简单到有点离谱:下载一个 docker-compose.yml,设一个加密密钥,然后一句 docker compose up -d,服务起来就能用 ⚡ MIT 协议,随便改、随便商用。

起来之后实际怎么用,一条线走下来其实很顺:新建一个 notebook,把几份 PDF、几个网页、再加段会议录音一股脑拖进去,它先帮你做成带来源的摘要;接着你像跟 NotebookLM 那样追问——这几份资料在哪打架了?某个结论依据在第几页?最后嫌看着累,一键转成多人对谈的播客,通勤路上听完。整条链路全程没有一个字节离开你的机器。

当然,别把它想成「点一下就和 Google 一模一样」。自托管意味着你得自己配环境:要么自带各家 API key,要么把本地模型先跑起来。开箱即用的顺滑程度,暂时也不一定追得上官方那版。它给你的不是「更省事」,而是「更可控」——数据攥在自己手里,模型自己挑,流程自己接。

想用 NotebookLM 那套能力、又一直卡在「资料不太想往上传」这步的,这个项目值得你这周末花半小时 docker 起来试一把 🚀

完整链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #NotebookLM #开源 #本地部署 #AI工具
