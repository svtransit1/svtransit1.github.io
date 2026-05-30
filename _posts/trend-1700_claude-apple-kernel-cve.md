---
layout: post
title: "很多人讲 AI 写代码的时候,第一反应是「省时间」。Apple 这两周悄悄发的一份安全公告,把这件事的天花板抬了一截——macOS 26.5 内核 APFS 漏洞的发现者那一栏,写的是 Claude。🔍"
date: trend 17:11:18 +0800
source: https://lagazetteia.fr/ia-generale/cve-2026-28952-claude-decouvre-une-faille-critique-du-noyau/
hero: /assets/1700_claude-apple-kernel-cve/trend_2026-05-26_1700_claude-apple-kernel-cve-hero.png
topic_tags: [cve, apple-security, claude-ai, anthropic, kernel-vulnerability, apfs, security-research, ai-safety]
---

CVE 编号:CVE-2026-28952。Apple 5 月 11 号已经修了,直到这两天才在中文圈热起来。Anthropic 的 Claude 第一次以「独立漏洞研究员」身份,被 Apple 记进了官方安全公告。

#这次抓的是APFS内核级漏洞 🛠️

过去 AI 在安全研究里大部分干的是「按用例跑」——给定 fuzzer 配置,自动化扫一遍,把人类写好的 attack vector 跑得更快。一种加速器。

这次的形态不一样。APFS 是 macOS 的文件系统内核模块,跑在 ring 0,出 bug 直接拿权限。Claude 找到的是一个完整的、可利用的、值得 Apple 单独发 CVE 的内核级漏洞——并不是事先有人类研究员发现、Claude 复现。整条线 Claude 自己跑通的。

#2024到2026这条曲线翘起来了 📈

2024 年大模型做安全研究的状态,大部分人记得的是「prompt 注入小把戏」。两年后,同一类模型能读懂 APFS 这种几十万行 C 代码、找到符合 CVE 标准的漏洞、把 PoC 写到 Apple 安全团队接受的程度。

这件事卡在大语言模型 + 静态分析 + 模糊测试这三条线的交叉点上——以前每一条线 AI 都参与一点点,现在是把整条流水线接通了:读代码 → 形成假设 → 写 PoC → 输出 advisory 草稿。🎯

#对安全研究员的影响是双向放大 ⚖️

不会是「AI 取代安全研究员」那种粗暴叙事。会是双向放大——

📉 门槛被压低了:会用 Claude 做漏洞挖掘的初级研究员,出报告速度起码 10 倍

📈 天花板被抬高了:顶尖研究员能跑的并发数,从过去几个项目变成几十个,人均产出再次跳一个量级

🛡️ 行业「合格门槛」会重新被定义:三年后入行的安全研究员,简历里没有「LLM 辅助流程」基本上是减分项

更深一层的信号——大公司的内部安全团队,以后会带着「常驻 Claude 实例」做漏洞挖掘。Apple 这次把 LLM 放进了 advisory 致谢栏,Microsoft、Google 这种体量的公司大概率明年内跟进。

#这是一道分水岭 🔓

5 月 11 号那份 patch 上线的时候,圈外没人注意。两周后中文圈才热起来,因为大家慢慢意识到这件事的尺寸:AI 在「内核级漏洞研究」这条最硬的安全工作线上,拿到了 Apple 体量公司的第一份官方致谢——这不只是 Claude 又会一件新事,是整条研究门槛被往下打了一寸。

下一份 advisory 里出现 Claude、GPT 或 Gemini 的名字,大概率会变成常态。2026 看的是「门槛被打破」;2027 看的是「比例多快上来」。🛡️

🔍 完整 CVE 记录 + 各家分析链接 · 第一条评论拿

关注 @svtransit1 · 写给真在用 AI 的人

#AI #Claude #安全研究 #Apple #CVE #硅谷中转站
