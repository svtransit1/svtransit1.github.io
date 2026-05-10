---
layout: post
title: "Addy Osmani 把 22 条「让 AI 编码 agent 像资深工程师那样干活」的技能,打包开源,GitHub 一周冲到 37.9k 星。"
date: 2026-05-10 21:13:12 +0800
source: https://github.com/addyosmani/agent-skills
hero: /assets/addy-osmani-agent-skills/2026-05-10_1800_addy-osmani-agent-skills-hero-raw.png
topic_tags: [claude-code, addy-osmani, agent-skills, engineering, ai-coding-agents]
---

仓库叫 agent-skills,内容就是 Markdown 文件,Claude Code、Cursor、Gemini CLI 都能直接装。每一条技能都是一段写给 agent 看的研发纪律,味道是按 Google《Software Engineering at Google》那本书来的。Addy 在 README 里把要解决的问题点得很直白:「AI agent 默认走最短路径」。意思是,如果不给它边界,它会跳过 review、跳过测试、跳过文档,直接交一个能跑就行的版本。

22 条技能分在六个阶段。挑几个有意思的:

**Define**——spec-driven development,要求 agent 先把需求写成可验证的 spec,再动代码。这一条是抗 AI 偷工减料的第一道闸门。

**Build**——里面有一条 doubt-driven development。AI 默认假装一切都懂,这条强制它先标出自己不确定的地方,再问、再写。光这一条,我觉得就值得装。

**Verify**——browser testing + debugging-and-error-recovery。Claude Code 写完代码不等于跑通,这一组让 agent 自己跑测试、读报错、回到上一步修。

**Review**——code-review、simplification、security-hardening、performance-optimization 各一条。最后那条 simplification 跟 Karpathy 那种「20 行能写完别写 50 行」的口味是一致的。

**Ship**——git workflow、CI/CD、deprecation、documentation、launch。最后这块对独立开发者最实用,大部分人 ship 那一步是裸奔的。

启动方式简单到不像话:Claude Code 一句 `/plugin marketplace add addyosmani/agent-skills`,装完就能用 `/spec`、`/plan`、`/build`、`/test`、`/review`、`/code-simplify`、`/ship` 七个 slash command。

这件事真正的信号在仓库之外。Addy Osmani 这种背景的人——长期在 Google / Chrome 性能那一线——开始把 AI coding 当成一种需要被工程纪律框住的产物,把 vibe-coding 玩具的那一面挤到边上去。AI agent 越来越能干,但它默认是个「速度最快、责任感最低」的实习生,你不给它一套规矩,它就会按那个默认值交活。

原始出处 · 第一条评论拿

关注 @svtransit1 · 写给真在用 AI 的人

#ClaudeCode #AI #AIagent #engineering #AI日报
