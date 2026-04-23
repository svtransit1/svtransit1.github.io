---
layout: post
title: "\"每天早上刷 10 个平台找话题,太累——有什么工具一键汇总?\"
date: 2026-04-23 15:15:00 +0800
source: https://github.com/sansan0/TrendRadar
hero: /assets/trendradar/2026-04-23_1400_trendradar-hero.png
topic_tags: [trendradar, open-source, chinese-platforms, trend-monitoring, litellm, devtools]
---

这问题在做中文 AI 内容、自媒体、舆情、投研的人头上都转过。大部分人的解法是收藏夹堆堆、订阅一堆 RSS、开十几个 tab 轮着刷——效率低、还总漏掉。

TrendRadar 是 GitHub 今天前列的项目,54.7k star,GPL-3.0,一天又涨了 969 颗。它做的事情很简单也很实在——11 个中文平台的热点一键聚合:微博、抖音、B站、知乎、百度热搜、今日头条、贴吧、澎湃、凤凰网、华尔街见闻、财联社。关键词 + 正则过滤,三种推送模式(每日汇总、实时 Top、增量),九个通知渠道(企微、飞书、钉钉、Telegram、邮件、Slack 等)全覆盖。

真正的亮点在 AI 分析层。接 LiteLLM,DeepSeek、GPT-4o、Claude 3.5 Sonnet、Gemini 都能接——不锁死单一供应商。每次拉完热点,AI 自动做三件事:排名变化分析、跨平台表现对比、舆论风向判断(正面 / 负面 / 争议)。等于把"刷平台"变成"读分析",省的不是时间,是信息处理的认知成本。

部署也干净。Docker 一条命令 docker run -d wantcat/trendradar 拉起,数据本地卷挂载;GitHub Actions 模式只要 fork + 填 secrets 就能定时跑,不用自己买云;本地 Python 也有 Win / Mac 脚本。

作者 v6.6.0(2026-03-28)刚发新版,加了自然语言兴趣过滤(直接说"我关心 AI 创业方向")和增强 HTML 报告(深色模式、tab 切换、正则搜索)。迭代节奏 1-3 个月一次大版本,稳。

对做 Chinese tech 内容的、跑舆情的、或者想从"被信息流推着走"换到"按规则主动筛"的人——这个 repo 值得 fork 下来直接部署。

关注 @svtransit1 · 每天都有有用的 AI 资讯

https://github.com/sansan0/TrendRadar

#AI #开源 #舆情监控 #AI工具
