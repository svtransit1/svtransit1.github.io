---
layout: post
title: "在 M4 Pro 上跑图生 3D,5 分 13 秒出一只带 PBR 贴图的 GLB。不用 CUDA,不租云,峰值 18GB 内存。"
date: 2026-04-23 00:10:00 +0800
source: https://github.com/shivampkumar/trellis-mac
hero: /assets/trellis-mac/2026-04-23_0010_trellis-mac-hero.png
topic_tags: [ai-3d, trellis, apple-silicon, metal, local-ai, image-to-3d]
---

TRELLIS 是微软放的那个图像 → 3D mesh 模型,原版只跑 NVIDIA CUDA。最近有人把它移植到 Apple Silicon,叫 trellis-mac,走 Metal 后端,317 star,MIT 协议。本地跑 3D 生成这条路一直没什么好方案——做游戏资产、角色手办、3D 打印模型的时候,每跑一次云 GPU 都是钱,排队还得排。

四条轴拉出来对比。

速度。官方 CUDA 在 H100 上大约 2-3 分钟一张,但那是理想排队。trellis-mac 在 M4 Pro(24GB)上 pipeline-type 512 是 5 分 13 秒(含冷启动),生成+烘焙 3 分 20 秒。慢一半左右,但不用排云端队,关上笔记本出门再回来接着跑。

成本。H100 按小时算,消费级云价 $2-4/hr;单张 mesh 摊下来大约 $0.10-0.20。一次看不出来,批量出 100 个资产就是 $20 起。M4 Pro 一次部署完就是自己的机器,后面每一次 0 元。重度用户的长期账,数量级不一样。

资产质量。输出 ~40 万顶点、~80 万三角形,烘焙后自动简化到 20 万面,带 base-color、metallic、roughness 三张贴图。够喂 Unity / Unreal / Blender 直接用,游戏场景里的道具级完全够,不用再手动 retopo。工业级 AAA 角色肯定还得过艺术家手——但这是所有生成式 3D 目前共同的天花板。

工作流。输入一张 PNG 单图就出货,命令行一条 python generate.py path/to/image.png。支持 --seed 固定结果、--pipeline-type 切 512/1024/1024_cascade 质量档、--texture-size 最高到 2048。对脚本化批量很友好,写个 shell loop 过一夜能出几十个。

门槛也说清楚:Apple Silicon(M1+)、24GB 以上统一内存、~15GB 硬盘装模型权重。HuggingFace 要 auth login,DINOv3 是 gated 模型(要在 HF 页上点同意),RMBG-2.0 是 CC BY-NC 4.0(商用留意)。sparse attention 没做融合,作者说 ~80 秒卡在这里——以后融合完速度还有空间。

所以谁该捡:有 M 芯片 Mac、偶尔做 3D 角色/道具/静态物件、不想月租云 GPU 的人。独立游戏开发者、手办/3D 打印做原型的、短视频博主做静态资产,都吃到这个红利。工业级批量资产还是得云跑——但 trellis-mac 把"能不能本地玩"这条路走通了。

安装四条命令:git clone、xcodebuild 下 Metal toolchain、hf auth login、bash setup.sh。跑起来一句 python generate.py photo.png --seed 123。

转给那个还在月租云 GPU 跑 3D 的朋友。

关注 @svtransit1 · 每天都有有用的 AI 资讯

https://github.com/shivampkumar/trellis-mac

#AI #3D #AppleSilicon #开源
