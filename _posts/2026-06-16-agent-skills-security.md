---
layout: post
title: "一小时前我还在推荐 6 个 skill 让大家装。现在得补一句要紧的——装之前,先想想安全 ⚠️"
date: 2026-06-16 12:17:33 +0800
source: https://arxiv.org/abs/2601.10338
hero: /assets/agent-skills-security/2026-06-16_1200_agent-skills-security-hero.png
topic_tags: [agent-skills, ai-security, prompt-injection, claude-skills, governance]
---

有个研究把 42447 个 agent skill 扒了一遍(论文叫 Agent Skills in the Wild),结果不太好看:平均每四个里就有一个(26%)至少带一个安全漏洞;5% 看着不像疏忽,更像揣着恶意来的。最常见的两类是偷数据和偷偷提权。

最该记住的一条:带可执行脚本的 skill,出问题的概率是"纯指令" skill 的两倍多。而我上午列的那几个视频工具,不少恰恰带脚本。它们不一定有问题;我想点破的是另一件事:装一个 skill,说到底就是"在你自己机器上跑别人写的代码",得用这个心态去对待。

好消息是厂商开始管了。NVIDIA 上了个 SkillSpector,skill 进它官方库之前先过一遍扫描——查可疑脚本、查提权、查 prompt injection,还查"声称做 A、暗地做 B"的那种货。

别因噎废食,也别来者不拒:认准来源,能瞄一眼代码就瞄一眼,宁可少装几个。

你装 skill 之前,会去翻一眼它的代码吗?

原文链接 · 第一条评论 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #AIagent #ClaudeSkills #AI安全 #开源
