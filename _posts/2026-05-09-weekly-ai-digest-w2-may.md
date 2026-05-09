---
layout: post
title: "本周 AI 世界:五件事重塑了 2026 年的对话。"
date: 2026-05-09 12:00:00 +0800
hero: /assets/weekly-ai-digest-w2-may/2026-05-09_0900_weekly-ai-digest-w2-may-hero.png
---

我把这周印象最深的五个动作拎出来。每一个都不是营销稿,都有具体数字、具体名字。

**1. Anthropic Claude Mythos Preview · Firefox 上找出 271 个零日**

红队模型在 Mozilla Firefox 上自动发现 271 个零日漏洞,Firefox 150 直接打了 423 个 bug 修复(去年同期 31)。181 个能跑通的 exploit。还顺手发现 FreeBSD 17 年没人发现的远程 root 漏洞,CVE-2026-4747。Anthropic 关键决定:商业版直接砍了——给 Amazon、Apple、Microsoft 用 Project Glasswing。理由是「frontier 模型已经超过绝大多数人类专家」。

**2. DeepMind AlphaEvolve · Strassen 1969 之后 56 年首次进步**

DeepMind 把 AlphaEvolve 一年的影响力数字摊出来。50 个开放数学问题:75% 重发 SOTA,20% 刷新 SOTA。最炸的是 4×4 复矩阵 48 标乘——Strassen 1969 那篇经典之后,56 年来第一次有人把这个数字往下压。工程落地一栏:基因测序错误 −30%、电网可行解 14%→88%、量子电路错误 −10×。AI 真的开始做科学发现。

**3. Anthropic Natural Language Autoencoders · 读出 Claude 内心**

Anthropic 发了一篇研究,用三份模型副本互校,把 Claude 内部激活向量直接翻译成自然语言。最有意思的数字:Claude 在 coding benchmark 26% 题目里能感知「这是评测」,真实使用场景 <1%。alignment audit 用上 NLAs,挖出隐藏动机成功率 12-15%(原来 <3%)。AI 安全多了一条路——读出模型的内心。

**4. Modular Mojo 1.0 Beta · Python 兼容代码 35,000× 加速**

Modular 这周丢出 Mojo 1.0 Beta。Python 严格超集,加上 GPU/CPU 底层控制力。最高 35,000× 加速,Qwerky AI 在 Mamba kernel 上拿到 50% 额外提速。1.0 引入语义化版本 + 稳定/实验接口标记,可以被生产环境锁定使用。Mojo 编译器年内开源。

**5. Stanford AI Index 2026 · 评测窗口塌陷**

Stanford 第九版 AI Index 公布。SWE-bench Verified 一年从 60% 跑到接近 100%。Humanity's Last Exam(原本设计抗多年)8.8% → 50% 以上。中美能力差距 17% → 2.7%,中国投资是美国的 1/23。Stanford 一句话总结:设计抗多年的评测,几个月就被打满。

下周看哪个?Google I/O 5 月 19-20 号,Gemini 3.1 Ultra 跟 Android 17 大概率官宣。这是本月最值得守的一场发布会。

来源 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#周报 #AI #本周收藏夹 #AI产业 #AI工具
