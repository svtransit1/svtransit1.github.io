---
layout: post
title: "把 prompt 当成模型来「训练」，听着像噱头。但微软真把它做成了一个开源工具。🧪"
date: 2026-05-29 15:15:40 +0800
source: https://github.com/microsoft/SkillOpt
hero: /assets/skillopt-train-agent-skills/2026-05-29_1245_skillopt-train-agent-skills-hero.png
topic_tags: [agent-skills, prompt-optimization, skillopt, microsoft, claude-code]
---

写过 Claude skill、调过 system prompt 的都懂那种感觉：agent 在某类任务上老翻车，你打开指令文档改两句，跑一下，凭手感再改两句。改好了不知道为啥好，改坏了也说不清哪一步坏的——全是玄学。

微软开源的 SkillOpt 想把这套玄学变成「训练」。模型权重一动不动，它优化的只是那份技能文档本身（你写给 agent 的 markdown 指令）。把 epoch、验证集这套机器学习的词搬过来：让一个优化器模型去读跑失败的轨迹、提出对文档的修改，再在留出的验证集上重跑，过了阈值才留下，没过就丢——一轮轮迭代，收敛出一个 best_skill.md。🧪

我觉得真正值钱的不是工具，是那个框架：它把「我感觉这样写更好」换成了「验证集说这样更好」。调 prompt 第一次有了能复现、改坏了会被拦住的工程流程，而不是一群人在 PR 里凭直觉吵。

转给那个还在纯靠手感调 prompt 的同事。

你现在调 prompt，是靠手感，还是已经有一套能验证对错的流程？

🧪 SkillOpt 仓库 (microsoft · 2.3k★) · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #AIagent #PromptEngineering #ClaudeCode
