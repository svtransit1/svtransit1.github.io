---
layout: post
title: "在笔记本上跑 GLM-5.2（744B）这件事，现在字面上是真的了——只是\"能跑\"和\"能用\"之间，隔着一个 0.05 tok/s。😅"
date: 2026-07-10 15:17:00 +0800
source: https://github.com/JustVugg/colibri
hero: /assets/colibri-glm52-laptop-not-usable/2026-07-10_1200_colibri-glm52-laptop-not-usable-hero.png
topic_tags: [local-llm, glm, inference, moe]
---

先说项目本身。有人写了个叫 colibri 的推理引擎，纯 C、零依赖、大概一千三百行代码，把 Zhipu 那个 744B 的 GLM-5.2 塞进了一台 25GB 内存的机器。魔法在 MoE 这层：模型虽然 744B，但每个 token 只激活 40B，于是作者干脆让绝大多数 experts 躺在硬盘上，用到哪个再 streaming 进内存。落盘的 int4 权重约 370GB，常驻内存只要 9.9GB，峰值 20GB 上下。就工程而言，这是个漂亮活。🛠️

接着是作者自己写在 README 里的老实数字，建议先深呼吸一下 👇

· WSL2、12 核、25GB 内存：冷启动解码 0.05–0.1 tok/s

· Intel Core Ultra 7：0.07–0.11 tok/s

· Framework 13 那颗 Ryzen AI 9 HX 370：0.37 tok/s

· 顶配 Apple M5 Max、128GB 统一内存：1.06 tok/s

作者也试了 MTP（多 token 预测）做投机解码，实测每次前向能吐 2.2–2.8 个 token——聊胜于无，但改变不了量级，真正的瓶颈始终是从 SSD 上把 experts 随机读进来那一下。

0.05 tok/s 是什么概念？一个 token 二十秒。你问一句话，它可能要憋上十几分钟才给你一段回答。就算是顶配那台 M5 Max 的 1 tok/s，也不过是让你盯着屏幕看它一个字一个字往外蹦。说"慢"都太客气了——这压根是另一种交互形态：你得把它当成寄信，不是聊天。✉️

这类"某某模型现在能在笔记本上跑了"的帖子，最近特别多，配合"自己拥有 vs 租算力"的情绪，很容易让人一冲动就去清 370GB 硬盘。所以我的读法是：colibri 真正证明的，是"前沿级模型可以不进显存、靠 SSD 流式跑起来"——这是实打实的本事，值得记一笔。但它现在是 proof of concept，不是生产力工具。你拿 370GB 硬盘换来的，是一个偶尔肯搭理你的派对魔术。🪄

真要落地，判断其实很干脆：你只想本地、离线、图个隐私，问一句等几分钟也无所谓——可以玩，而且是认真能玩的那种。想拿它写代码、跑 agent 工作流、要交互速度——省省吧，租 GPU 或者调 API 目前还是唯一现实解。

顺便，这项目挂上去十来个小时就近千颗星，热度是真的。但下次再看到"能在笔记本上跑 XX 大模型"的标题，不妨多问一句：跑，是多少 tok/s 的跑？🧐

完整链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #LocalLLM #GLM #AI工具
