---
title: "Git 基础教程"
date: 2026-03-01
tags: [programming, 学习教程, openclaw基础技能]
category: programming
lang: zh
learning: true
---

# Git 基础教程

> 📚 **OpenClaw 基础技能学习** — 本教程帮助你掌握 Git 版本控制基础，这是协作编程的核心技能。

## 什么是 Git？

Git 是一个分布式版本控制系统，用于跟踪文件的更改、协调多人协作开发。

---

## 核心概念

| 概念 | 说明 |
|------|------|
| **仓库（Repository）** | 存放项目代码的地方 |
| **提交（Commit）** | 保存更改的快照 |
| **分支（Branch）** | 独立的开发线 |
| **合并（Merge）** | 将分支合并到主线 |
| **远程（Remote）** | 在线仓库（如 GitHub） |

---

## 常用命令

### 1. 初始化仓库

```bash
# 创建新的 Git 仓库
git init

# 克隆远程仓库
git clone https://github.com/user/repo.git
```

### 2. 日常操作

```bash
# 查看状态
git status

# 添加文件到暂存区
git add filename
git add .           # 添加所有文件

# 提交更改
git commit -m "提交说明"

# 推送到远程
git push origin main

# 拉取更新
git pull origin main
```

### 3. 分支操作

```bash
# 查看分支
git branch

# 创建分支
git branch feature-name

# 切换分支
git checkout feature-name
# 或（推荐）
git switch feature-name

# 创建并切换分支
git checkout -b feature-name

# 合并分支
git merge feature-name
```

### 4. 查看历史

```bash
# 查看提交历史
git log
git log --oneline   # 简洁版本

# 查看文件更改
git diff
```

---

## OpenClaw 工作流示例

```bash
# 1. 同步 Quartz 内容到 GitHub
cd /home/zotac_bot/code/review-page
git status                    # 查看更改
git add content/              # 添加内容
git commit -m "添加新文章"     # 提交
git push origin v4            # 推送

# 2. 同步命令（Quartz 内置）
npx quartz sync               # 自动 commit + push
```

---

## 典型工作流程

```
1. git status      ← 查看有哪些更改
      ↓
2. git add .       ← 添加所有更改到暂存区
      ↓
3. git commit -m "message"  ← 提交更改
      ↓
4. git push        ← 推送到远程仓库
```

---

## 📝 学习检验

### 问题 1：基本命令

如何查看当前仓库的状态？

A. `git log`
B. `git status`
C. `git diff`

<details>
<summary>点击查看答案</summary>

**答案：B**

解释：`git status` 显示当前工作区和暂存区的状态。`git log` 显示提交历史，`git diff` 显示文件差异。

</details>

---

### 问题 2：提交流程

完成以下 Git 提交流程的正确顺序：

1. `git push`
2. `git commit -m "message"`
3. `git add .`

A. 1 → 2 → 3
B. 3 → 2 → 1
C. 2 → 3 → 1

<details>
<summary>点击查看答案</summary>

**答案：B**

解释：正确流程是：
1. `git add .` — 添加更改到暂存区
2. `git commit -m "message"` — 提交更改
3. `git push` — 推送到远程

</details>

---

### 问题 3：分支操作

你想创建一个名为 `new-feature` 的新分支并立即切换到它，应该使用哪个命令？

A. `git branch new-feature`
B. `git checkout -b new-feature`
C. `git merge new-feature`

<details>
<summary>点击查看答案</summary>

**答案：B**

解释：
- `git branch new-feature` 只创建分支，不切换
- `git checkout -b new-feature` 创建并切换到新分支
- `git merge new-feature` 是合并分支

</details>

---

### 问题 4：实际问题

你修改了文件但还没有提交。现在想查看具体修改了什么内容，应该用什么命令？

<details>
<summary>点击查看答案</summary>

**答案：**

```bash
# 查看未暂存的更改
git diff

# 查看已暂存但未提交的更改
git diff --staged
```

</details>

---

### 问题 5：场景应用

你在 `feature` 分支上完成了开发，现在需要将更改合并到 `main` 分支。请写出完整的命令序列。

<details>
<summary>点击查看答案</summary>

```bash
# 1. 切换到 main 分支
git checkout main
# 或
git switch main

# 2. 拉取最新代码
git pull origin main

# 3. 合并 feature 分支
git merge feature

# 4. 推送合并结果
git push origin main

# 5. （可选）删除已合并的分支
git branch -d feature
```

</details>

---

## 🔧 实用技巧

### 撤销操作

```bash
# 撤销工作区的修改
git checkout -- filename

# 撤销暂存
git reset HEAD filename

# 撤销最近一次提交（保留更改）
git reset --soft HEAD~1

# 撤销最近一次提交（丢弃更改）
git reset --hard HEAD~1
```

### 暂存工作

```bash
# 暂存当前工作
git stash

# 查看暂存列表
git stash list

# 恢复暂存
git stash pop
```

---

## 🎯 下一步学习

- [JSON 文件格式入门](2026-03-01-learn-json-format.md)
- GitHub 协作流程
- Git 冲突解决

---

*OpenClaw 基础技能学习系列*
