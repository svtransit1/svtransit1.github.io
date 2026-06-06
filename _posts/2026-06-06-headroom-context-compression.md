---
layout: post
title: "「每个月光是 API 账单就贵得肉疼,有没有办法在不换模型的前提下,把 token 用量压下来?」💸"
date: 2026-06-06 09:17:22 +0800
source: https://github.com/chopratejas/headroom
hero: /assets/headroom-context-compression/2026-06-06_0900_headroom-context-compression-hero.png
topic_tags: [headroom, context-compression, token-cost, llm-infra, open-source]
---

最近 GitHub 上蹿得很快的一个开源项目 Headroom,给的就是这个答案。它的位置很巧——夹在你的应用和大模型中间,把要发出去的上下文先压一道再转给模型,答案尽量保持不变。说白了,就是帮你把「废话」删干净再发。

先看它压得有多狠。一次 SRE 排障,六万五千多 token 的日志压到五千出头,砍掉九成二;一百条代码搜索结果,从一万七千多压到一千四,同样九成二;GitHub issue 分类那种场景,五万四压到一万四,省七成多。📉

你可能会问,那我自己 truncate 一刀切不就行了?问题恰恰出在「一刀切」——日志里最关键的那行 FATAL,很可能正好落在你砍掉的那半边。Headroom 的卖点是先看懂内容再下手:该留的错误码、函数签名留着,把重复的、模板化的、机器读了也没用的噪音挑出去。官方那个 demo 里,一万出头的 token 压到一千二,那行 FATAL 报错照样被模型抓了出来。

按现在主流模型的价钱,输入便宜的也要几块钱一百万 token,贵的十几块。最好的场景砍掉九成,等于这部分账单直接打一折;差一点的场景也能省一半左右——常年跑 agent、动不动喂一长串日志的人,一个月省下来真不是小数。

那答案会不会被压坏?这才是大家最担心的。官方贴的几个测试里:GSM8K 数学题,压前压后都是 0.870,一分没掉;TruthfulQA 还从 0.530 微涨到 0.560。⚠ 不过这些都是作者自己跑的分,第三方还没复现,先看个方向就好。

它怎么做到的?里头有个 ContentRouter,先认一下你发的是什么——JSON、代码、还是大段文字——再分给对应的压法:结构化数据走 SmartCrusher,代码走 CodeCompressor,纯文本交给一个 HuggingFace 小模型,还有一路专门稳住开头那段,好让 provider 的 KV cache 命中。怕信息丢的话,它还留了个可逆模式,能把原文再还回来——真要审计、回看原始日志时一键还原,不至于把证据也一起压没了。

上手也不挑姿势,四种随你选:当 Python 库直接 compress;起个 proxy(headroom proxy --port 8787)让所有请求过一道;直接把 agent 包起来(headroom wrap claude,Cursor、Aider、Copilot CLI 都认);或者当 MCP server 装。一句 pip install headroom-ai 全家桶就齐。🛠️

当然别当万能药。压缩率在不同内容上跳得厉害,好的到九成二,差的(比如整库浏览)只有四成七,具体省多少得看你喂什么。它说到底是有损的,除了可逆模式,丢掉的就是丢了;几个 benchmark 上没掉精度,不代表你的活也不掉。而且它得跑一个本地进程,沙箱、serverless 用不了,Windows、Linux、Docker 的一些路径作者也说还没充分验证。

所以别急着换更便宜的模型,先回头看看:你平时喂给模型的上下文,真正有用的能占几成?剩下那些,可能正不声不响地替你烧着钱。🤔

来源 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #LLM #ClaudeCode #AI工具 #降本
