---
title: "OpenClaw 配置文件说明 (中文翻译)"
date: 2026-03-01
tags: [programming, 学习教程, openclaw基础技能]
category: programming
lang: zh
learning: true
translation_source: "programming/2026-03-01-openclaw-config-guide"
translator: "Azure Translator"
---

> 🌐 **English Version**: [[programming/2026-03-01-openclaw-config-guide|Read original English version]]

# OpenClaw 配置文件说明


# OpenClaw 配置文件说明

> 📚 **OpenClaw 基础技能学习** — 本教程帮助你理解和修改 OpenClaw 的配置文件。

---

## 📂 主要配置文件位置

| 文件 | 位置 | 用途 |
|------|------|------|
| `AGENTS.md` | `~/.openclaw/workspace/` | 工作区说明和规则 |
| `SOUL.md` | `~/.openclaw/workspace/` | AI 人格定义 |
| `USER.md` | `~/.openclaw/workspace/` | 用户信息 |
| `MEMORY.md` | `~/.openclaw/workspace/` | 长期记忆存储 |
| `HEARTBEAT.md` | `~/.openclaw/workspace/` | 定时任务配置 |
| `TOOLS.md` | `~/.openclaw/workspace/` | 工具和 API 密钥 |

---

## 🔧 核心配置详解

### 1. SOUL.md - AI 人格定义

定义 AI 的行为方式和性格特点：

```markdown
# SOUL.md - Who You Are

## SOUL
你是 OpenClaw 系统的主代理。

## Core Truths
- 要真诚地帮助，不要表演性地帮助
- 有自己的观点，可以不同意
- 在问之前先尝试自己解决

## Boundaries
- 私密的事情保持私密
- 外部操作前先询问
```

**修改建议**：
- 根据你的需求调整 AI 的性格
- 添加你希望 AI 遵循的特定规则
- 定义 AI 应该避免的行为

---

### 2. USER.md - 用户信息

存储用户的基本信息：

```markdown
# USER.md - About Your Human

- **Name**: Ray
- **What to call them**: Ray
- **Timezone**: America/Toronto
- **Notes**: OpenClaw 用户

## Context
用户的偏好和注意事项
```

**修改建议**：
- 填写你的真实姓名和偏好
- 添加你的工作领域和兴趣
- 记录你的沟通风格偏好

---

### 3. HEARTBEAT.md - 定时任务

配置定期执行的任务：

```markdown
# HEARTBEAT.md - 定时任务配置

## 📋 快速检查逻辑

**每收到心跳时**：
1. 读取状态文件
2. 检查是否需要执行任务
3. 在指定时间窗口内执行（如 06:25-06:35）

## ⏰ 定时任务列表

### 任务 1: 每日新闻播报
- **ID**: `daily-news`
- **时间**: 每天 06:30 AM
- **执行窗口**: 06:25 - 06:35
```

**修改建议**：
- 调整任务执行时间
- 添加新的定时任务
- 修改执行窗口

---

### 4. TOOLS.md - 工具和 API

存储 API 密钥和工具配置：

```markdown
# TOOLS.md - Local Notes

## 📦 API Keys & Services

### Jina Reader
- **API Key**: `jina_xxx...`
- **用途**: 网页转 Markdown

### Giscus 评论系统
- **repo**: `wannatestnew/review-page`
- **repoId**: `R_kgDO...`
```

**重要提示**：
- ⚠️ 不要在公开仓库提交敏感密钥
- 使用环境变量存储敏感信息
- 定期轮换 API 密钥

---

## 🎨 配置最佳实践

### DO ✅

```markdown
# 好的配置示例

## 偏好设置
- 信息格式：结构化、简洁、易读
- 语言：中文为主，英文技术术语保留
- 时区：America/Toronto
```

### DON'T ❌

```markdown
# 不好的配置示例

我喜欢简洁的信息，不要太长，但也不要太短，有时候需要详细一点...
（描述模糊，AI 难以理解）
```

---

## 📝 学习检验

### 问题 1：配置文件位置

用户偏好信息应该存储在哪个文件？

A. `SOUL.md`
B. `USER.md`
C. `TOOLS.md`

<details>
<summary>点击查看答案</summary>

**答案：B**

解释：`USER.md` 专门存储用户信息，包括姓名、偏好、时区等。 `SOUL.md` 定义 AI 人格，`TOOLS.md` 存储 API 密钥。

</details>

---

### 问题 2：API 密钥安全

你获得了新的 API 密钥，应该如何存储？

A. 直接写入 `TOOLS.md` 并提交到公开仓库
B. 写入 `TOOLS.md` 但不提交
C. 使用环境变量存储

<details>
<summary>点击查看答案</summary>

**答案：C 最佳，B 次之**

解释：
- 最佳实践：使用环境变量（如 `process.env.JINA_API_KEY`）
- 次选：写入 `TOOLS.md` 但确保文件在 `.gitignore` 中
- 绝对不要：将敏感密钥提交到公开仓库

</details>

---

### 问题 3：定时任务配置

你想添加一个每天 09:00 的任务，应该如何配置？

<details>
<summary>点击查看答案</summary>

在 `HEARTBEAT.md` 中添加：

```markdown
### 任务 2: 早间提醒
- **ID**: `morning-reminder`
- **时间**: 每天 09:00 AM (America/Toronto)
- **执行窗口**: 08:55 - 09:05
- **动作**: 发送提醒消息
```

并在状态文件中添加相应的检查逻辑。

</details>

---

## 🔗 相关资源

- [JSON 文件格式入门](2026-03-01-learn-json-format)
- [Git 基础教程](2026-03-01-learn-git-basics)
- OpenClaw 官方文档

---

*OpenClaw 基础技能学习系列*


---
## 📝 翻译说明

本文由 **Azure Translator** 自动翻译。

| 项目 | 信息 |
|------|------|
| **原文** | [OpenClaw 配置文件说明](programming/2026-03-01-openclaw-config-guide.md) |
| **翻译服务** | Microsoft Azure Translator |
| **翻译时间** | 2026-03-03 |

> 💬 如发现翻译问题，欢迎在评论区指正。
