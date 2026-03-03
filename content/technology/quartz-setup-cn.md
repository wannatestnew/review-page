---
title: "How I Built This Digital Garden (Quartz 4) (中文翻译)"
date: 2026-02-28
tags:
  - technology
  - tutorials
  - quartz
translation_source: "technology/quartz-setup"
translator: "Azure Translator"
---

> 🌐 **English Version**: [[technology/quartz-setup|Read original English version]]

# How I Built This Digital Garden (Quartz 4)


# 我的Quartz 4设置指南

本说明记录了使用**Quartz 4**、**Obsidian**和**GitHub Actions**搭建本网站的过程。

## 🏗️ 核心工作流程
要发布笔记，我遵循一个三步系统：
1. **编辑：** 我用 **Neovim** 或 **Obsidian** 写 Markdown。
2. **生成器：** **Quartz 4** 将那些 Markdown 文件变成了一个网站。
3. **主机：** **GitHub Pages** 向全世界提供文件。

## 🚀 关键指令
我在我的 Arch Linux 终端中使用以下命令来管理网站：

|指挥 |目的 |
|:--- |:--- |
|'NPX 石英同步' |**“发布”按钮。** 从GitHub拉取内容，提交本地更改，并推送到网页。|
|“NPX石英建造” |本地搭建网站以检查错误。|
|“NPX 石英建造——发球” |在“http://localhost:8080”开始本地预映。|

## 🛠️ 关键故障排查
如果网站显示**404错误**，我会检查以下三点：

1. **部署工作流程：** 确保“.github/workflows/deploy.yml”存在且权限正确（“pages： write”）。
2. **GitHub 设置：** 访问“设置>页面”，确保**源代码**设置为“GitHub Actions”。
3. **基础URL：** 在“quartz.config.ts”中，“baseUrl”必须与我的GitHub仓库子文件夹（例如“wannatestnew.github.io/review-page”）匹配。

---

## 📽️ 参考资料
* **教程：** [如何使用Quartz免费发布你的笔记]（https://www.youtube.com/watch?v=6s6DT1yN4dw） 作者：Nicole van der Hoeven。
* **文档：** [Quartz 官方文档]（https://quartz.jzhao.xyz/）

> “数字花园是不断演变的笔记集合，而不是一系列完成的帖子。”


---
## 📝 翻译说明

本文由 **Azure Translator** 自动翻译。

| 项目 | 信息 |
|------|------|
| **原文** | [How I Built This Digital Garden (Quartz 4)](technology/quartz-setup.md) |
| **翻译服务** | Microsoft Azure Translator |
| **翻译时间** | 2026-03-03 |

> 💬 如发现翻译问题，欢迎在评论区指正。
