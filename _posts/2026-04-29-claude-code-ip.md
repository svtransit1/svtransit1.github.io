---
layout: post
title: "\"我用 Claude 写的代码,到底归谁?\"
date: 2026-04-29 15:14:35 +0800
source: https://legallayer.substack.com/p/who-owns-the-claude-code-wrote
hero: /assets/claude-code-ip/2026-04-29_1500_claude-code-ip-hero-raw.png
topic_tags: [claude-code, ip, copyright, legal, gpl]
---

短答案是:你以为是你的,可能不是。这条法律解读上 HN 顶到 343 分,作者是执业律师,三个真实风险叠在一起,大部分中文圈 dev 都没意识到。版权这一关,美国 Copyright Office 已经判过了 — 纯 AI 生成的代码缺乏"有意义的人类创作",根本拿不到版权,意思是别人复制你 AI 写的代码,你不一定能告。雇主合同这一关更麻烦,大部分公司的 employment agreement 写得很宽,员工在职期间用任何工具产出、跟公司业务相关的代码 IP 都归公司,你周末用 Claude Code 做的开源副业,如果跟主业沾边,公司理论上有 claim 权。GPL 污染这一关风险更隐蔽,Claude / Copilot 的训练数据里有大量 GPL 代码,模型万一 reproducing 出一段函数到你的商用代码,整个项目可能被"传染"成 GPL,衍生作品全部要开源 — 2022 年底 Doe v. GitHub 那个 class action 就是围绕这个问题打的,2023 年仍在审理。三件事看上去离自己很远,但任何在外企、出海团队、或者接商单写代码的人,都已经在风险半径里。中文圈 dev 圈对这件事的认知普遍偏低 — 大部分人觉得"我让 AI 写的就是我的",或者"反正自己用没事"。这种自信在 2023 年还能蒙混过去,2026 年代码进入了真实合同跟商业流水,法律责任已经开始落到具体项目上。国内已经有团队为了一段被 AI 不小心翻出来的 GPL 函数,被 ToB 客户要求重写整个模块。

具体怎么补?四件事这周做完比写两篇技术文章对你长期更值。license scan 必须上,FOSSA / Snyk / Black Duck 扫一下 AI 代码片段是否跟 GPL/AGPL 高相似度,商用 release 前过一遍成本可控。commit log 跟 prompt history 留下来,这是证明"人类有意义参与"的最直接证据,不要让 AI agent 一键 merge,至少 sign-off 一次。employment IP 那一条要看清楚,做副业的话主动跟 HR 沟通声明 prior invention,把私人项目排除在外,这一步不做以后真出事没法举证。商用合同的 commercial terms 要 verify,Anthropic 跟 OpenAI 的 API ToS 都明确写了输出责任在用户,所以客户付钱让你交付代码时,合同里"代码版权、法律责任、第三方 IP 不侵权"三条要写清楚。AI coding 已经从玩具变成生产力工具,你的代码迟早会进合同、产品、收入流。法律灰色地带不会自动消失,只会在第一次出事的时候变成你的麻烦 — 这周抽 30 分钟把这四件事 review 一遍,远比再读一篇技术文章值得。如果你是公司技术 lead,这事可以推动一次内部 AI coding 使用规范 — 把"agent 必须 sign-off"、"商用 release 必须 license scan"、"敏感项目禁止用云端 AI"这种边界写成明文,事先建立规则比事后救火便宜得多。Anthropic / OpenAI 早晚也会被迫给企业版加更明确的 IP 保证条款,但那是之后的事,自己的代码现在就要负责。

转给那个用 Claude Code 写商用代码但从来没看过 license 的同事 ↓

源链接在评论区 👇

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #版权 #开源 #AI日报
