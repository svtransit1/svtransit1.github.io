---
layout: post
title: "输入一句话,十分钟后拿到一条成片。Pixelle-Video 把整条 AI 视频流水线拆得很彻底——5.2k star,Apache 2.0,完全免费跑得起来。"
date: 2026-04-22 21:09:00 +0800
source: https://github.com/AIDC-AI/Pixelle-Video
hero: /assets/pixelle-video/2026-04-22_1830_pixelle-video-hero.png
topic_tags: [ai-video, comfyui, ollama, open-source, pixelle, alibaba-aidc]
---

最近在看 AI 视频拼接流水线的开源方案,发现市面上能用的基本都是 SaaS:Pictory、Invideo、Runway,月费 $20 起跳,素材还锁在它云里。Pixelle 这个 repo 是阿里 AIDC-AI 开的,思路反过来——全链路给你摊开,每个组件都能换。

你给它一个话题或一段文案,它自己走完整条链路。先让 LLM 写脚本、规划分镜;然后调 ComfyUI 逐帧生图,默认吃 FLUX 或 WAN 2.1;接着上 TTS 配音,Edge-TTS、Index-TTS 都行,想换音色传一段参考音频就能做声线克隆;再铺一条背景乐;最后 ffmpeg 合成 MP4 吐到 output/ 目录。

成本这一条是最实在的。纯本地跑:Ollama 接 LLM、ComfyUI 接图,整套 0 元。不想自己配 GPU 就上 Qwen + RunningHub 云端,中间档。OpenAI + RunningHub 全云最贵。作者自己推的是 Qwen API + 本地 ComfyUI——便宜、稳、延迟低。

装起来两条路。Windows 直接下一键集成包,解压就跑,不用装 Python / uv / ffmpeg。Mac / Linux 就 git clone 完 uv run streamlit run web/app.py 拉个本地 web UI。ComfyUI 是前置依赖,但做过 AI 绘图的机器基本都装过,不算新门槛。

输出支持 9:16 / 16:9 / 1:1 三种比例,1 月刚加的 motion transfer 模块能让图动起来,数字人口播流水线也接上了。demo 跑了三路内容——人文纪实、文化解构、科学思辨,横屏竖屏都有成片。

这种"给个主题就出成片"的工具以前都是付费 SaaS 的地盘。Pixelle 把整条流水线完整开源,门槛从订阅变成一次本地部署。

关注 @svtransit1 · 每天都有有用的 AI 资讯

https://github.com/AIDC-AI/Pixelle-Video

#AI #AI视频 #开源 #ComfyUI
