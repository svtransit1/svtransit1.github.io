---
layout: post
title: "家用康复治疗有一个老问题：医生开的动作做对的人不多，没人盯着。这周 arxiv 上一篇 3 页短文给了一个值得讨论的工程方向。"
date: 2026-04-26 01:46:32 +0800
source: https://arxiv.org/abs/2604.21154
hero: /assets/physio-multi-agent/2026-04-26_0140_physio-multi-agent-hero.png
topic_tags: [medical-ai, multi-agent, mediapipe, rehab, research-direction]
---

不是已经跑出来的系统，是一份研究架构提案——4 月 22 日刚提交到 IEEE ICDH。作者提出用四个分工 agent 把家庭物理治疗的 loop 闭起来：

第一个 agent 读医生的临床记录，提取关节运动学约束（哪个关节、哪个角度、哪种禁忌）。第二个 agent 用基础视频生成模型，按这些约束生成「针对你这个人」的示范视频，替代千篇一律的预录片。第三个 agent 用 MediaPipe 做实时姿态估计。第四个给你即时纠错反馈。

老实说，这是个提案，不是产品。论文只有 3 页 2 张图，没有实验数据，没有患者队列，没有部署。作者写的是「我们将提出临床评估方案」——未来时。

但架构本身是清的：把 LLM、视频生成、视觉 pipeline 这三个目前各自最强的能力，绑在一个具体临床问题上。这种思路比再发一篇通用 agent 框架论文有用多了——前者解决「家用康复合规性」这个真实痛点，后者只是在已知问题上多加一层抽象。

值得记下来等下一次更新。看作者会不会在 ICDH 发出真实数据，还是又一份 vaporware。

完整链接 · 评论区取 ↓

关注 @svtransit1 · 每天都有有用的 AI 资讯

#AI #医疗AI #多智能体 #研究方向 #AI日报
