---
layout: post
title: "阿里 AIDC 把\"AI 全自动短视频\"做成一个开箱即用的工具，10K star，直接对标手搓视频流水线。"
date: trend 17:14:11 +0800
source: https://github.com/AIDC-AI/Pixelle-Video
hero: /assets/1700_pixelle-video/trend_2026-05-04_1700_pixelle-video-hero-raw.png
topic_tags: [pixelle, video-gen, comfyui, alibaba, automation]
---

Pixelle-Video 这个礼拜在 GitHub 上挺热，Alibaba AIDC 团队出品。一句话定位：输入一个主题，自动跑 文案 → 配图 → TTS → BGM → 合成 的全套 pipeline。零剪辑经验，竖屏横屏都行，Windows 还有整合包。最近一次更新刚加了"动作迁移"和"数字人口播"两个模块。底层走的是 ComfyUI，所以模型、TTS、视频引擎都可以替换。

跟我自己最近用的工具放一起比一下，三条路各有各的偏好，分别对应不同的内容工作流形态。

▍Pixelle-Video — 一键全自动

底层是 ComfyUI 架构 + 模块化插件。LLM 这一截可以接 GPT、DeepSeek、Qwen、Ollama 任意一个；TTS 支持 Edge-TTS、Index-TTS、ChatTTS、各种本地 TTS 都行；图片可以走 Nano Banana、FLUX 或者你自己的 ComfyUI 图生工作流；视频段可以接 WAN 2.1。云端跑可以接 RunningHub 的 48G 显存机器。最近还内置了 FAQ 侧边栏、固定脚本的多种分割方式、批量任务历史，新加的"数字人口播"对做面对镜头的财经/科技/教程号特别友好，"动作迁移"则是给跳舞类、运动类内容直接补了一条捷径。强项很明显 —— 速度和门槛。一个主题丢进去，几分钟一条短视频出来，整团队不用懂 ffmpeg、不用碰命令行。弱项也明显 —— 节奏被稀释。自动配图按句拆分，每个 beat 多长由 LLM 推断决定，作者的意图很难精确压进去；模板做风格统一，但模板本身就会让所有视频"长得像同一团人做的"。

▍Runway / Higgsfield — 专业控

按镜头出工，扣帧到秒，定价按生成时长收钱，单条成本不便宜。强项是镜头质感、运动连续性、电影感、二次曝光这种高阶视效。弱项是装配速度慢 —— 一个 60 秒短视频可能要拼半小时，主题快速测试这条路不通。适合品牌广告、单条要打透的内容、对画面美学要求高的纪录性短片。

▍HyperFrames + Qwen3 + codex-image-gen — 自己手搓

HTML 写 beat、GSAP 控时间轴、Qwen3 Dylan 本地配音、ComfyUI / Codex 出图、ffmpeg 拼接 + loudnorm 对齐音量。强项是分镜和节奏完全可控、可以踩 0.3 秒精度做音画同步、单帧重渲不用重跑整条 pipeline、可以把品牌的视觉语言固化成模板。弱项是要写代码、要懂音频响度规范、要会处理 hyperframes 的双时间轴漂移、调试链很长，第一次跑通至少要一两天。

谁该用 Pixelle？想出量、想测主题反应、做 SEO 内容、走频次的竖屏号、本地化短视频代运营 —— 自动化的"够用"对这群人最划算。每天五条十条都不是问题。谁不该用？要做有作者风格的内容、单条要打透 retention 的、要把品牌视觉当壁垒的 —— 全自动 pipeline 出来的东西"看着像 AI 做的"，算法识别得到，观众也识别得到，单条 5 秒内就被划走。

从经济角度顺手算一笔账。Pixelle 走 Edge-TTS + Nano Banana + 自家 LLM 的最低组合，单条 60 秒短视频的边际成本可以压到几毛人民币以内，主要是 LLM token 和图片生成。Runway 那条路同样长度的视频，按 Standard plan 每月配额能出大概几十条，单条折算下来要小几十块；按生成时长付费的玩法更贵。手搓 HyperFrames 那条路靠本地 mlx-audio + 本地 codex-image-gen，单条只烧电费，但前期工程时间是真金白银的钉子户成本。这三种成本结构对应三种内容业务模型 —— 量、质、定制 —— 没有一个会吃掉另两个。

更大的信号比工具本身重要。自动化短视频从"研究项目"走到"工具产品"这一步，国产团队跑得明显比海外快。从 Pixelle-Video 这种端到端开源工具，到背后 ComfyUI 生态本身的繁荣，中文 AI 视频赛道未来一年会涌进非常多新玩家。工具能力只是入场券，编排节奏、视觉语言和审美才是真正的壁垒。下半年看谁能在批量化和作者风格之间踩出第三条路。

完整链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #视频生成 #ComfyUI #DeepSeek #AI工具
