---
layout: post
title: "【原来 Claude Code 已经能自己写脚本、一次指挥上千个子代理了】🧩"
date: 2026-05-30 09:25:09 +0800
source: https://claude.com/blog/introducing-dynamic-workflows-in-claude-code
hero: /assets/claude-code-dynamic-workflows/2026-05-30_0900_claude-code-dynamic-workflows-hero-6.png
topic_tags: [claude-code, dynamic-workflows, subagents, ultracode, anthropic]
---

很多人还停留在「一个 agent 一条线干到底」的印象里。但 Anthropic 上周跟 Opus 4.8 一起放出的 Dynamic Workflows（动态工作流），把这件事彻底改了——而且这两天才有人开始认真聊它。我翻了官方文档，给你讲清楚它是什么、怎么开、拿来干什么。

它到底是什么？你描述一个任务，Claude 当场写一段 JavaScript 编排脚本，丢给一个 runtime 在后台跑，你的对话窗口不会被占住，回头给你一份整合好的答案。编排逻辑不用你手写，Claude 自己生成。

举个例子你就懂：你说「帮我审一遍这个服务有没有安全漏洞」，它不会自己一行行读到天黑，而是当场规划——派一批 agent 分头扫不同模块、不同漏洞类型，几路并行，你这边该干嘛干嘛，回头收一份汇总。

规模是真的猛：一次最多拉起 1000 个子代理，同时并行的上限是 16 个。Claude 接到 prompt 后自己把任务拆成子任务，扇出去并行处理。

最该划重点的是验证那一层：多个 agent 从不同角度解同一个问题，然后另一批 agent 专门去「反驳」前面的结论，一轮轮对抗到答案收敛，才把结果合并。拍脑袋的、似是而非的，在合并前就被筛掉——一群 agent 互相验过，而不是一个 agent 自说自话。

怎么开（这是你能马上用上的部分）：

· 最省事一句 /effort ultracode。它把推理强度拉到 xhigh，并打开自动编排——Claude 自己判断任务值不值得开 workflow。

· 一个请求能串成好几个 workflow：一个先读懂代码、一个动手改、一个专门验证。

· 想手动触发，也可以直接让它「建一个 workflow」。

拿来干什么最划算？官方和早期用户给的场景很集中：全代码库的 bug 搜索、安全审计、大规模 migration、以及任何「答错代价很高、需要从多个角度反复确认」的关键改动。

两个前提先记住：目前是 research preview，所有付费方案都能用（Pro / Max / Team / Enterprise，API、Bedrock、Vertex、Foundry 全覆盖）；以及它比普通 session 烧的 token 多不少，先拿范围明确的任务试，别一上来就让它扫整个仓库。

说句实在的，这套「扇出去并行、互相反驳、收敛了才信」的打法，本来就是认真用 agent 的人手动在做的事——以前你得自己开十个窗口、自己当裁判，现在被收进了一条命令里。

你下次写代码，会不会试试把「判断对错」这件最费神的活，从一个模型扩成一群模型互查？

🧩 Anthropic 官方 Dynamic Workflows 文档 + 公告 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#Claude #ClaudeCode #AIagent #AI
