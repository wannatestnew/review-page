---
title: "Markdown 入门教程 (中文翻译)"
date: 2026-03-01
tags: [programming, 学习教程, openclaw基础技能]
category: programming
lang: zh
learning: true
translation_source: "programming/2026-03-01-learn-markdown-basics"
translator: "Azure Translator"
---

> 🌐 **English Version**: 

# Markdown 入门教程

# Markdown 入门教程

> 📚 **OpenClaw 基础技能学习** — Markdown 是轻量级标记语言，是编写技术文档、笔记和博客的标准格式。

---

## 什么是 Markdown？

Markdown 是一种简洁的文本格式，可以转换为 HTML 等格式。 它的设计理念是：

- 易读易写
- 纯文本格式
- 可转换为多种格式

---

## 基本语法

### 1. 标题

```markdown
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```

### 2. 段落和换行

```markdown
这是一个段落。

这是另一个段落。

第一行  
第二行（两空格换行）
```

### 3. 强调

```markdown
**粗体文本**
*斜体文本*
***粗斜体***
~~删除线~~
```

**效果**：
- **粗体文本**
- *斜体文本*
- ***粗斜体***
- ~~删除线~~

---

## 列表

### 无序列表

```markdown
- 项目一
- 项目二
  - 子项目一
  - 子项目二
- 项目三
```

**效果**：
- 项目一
- 项目二
  - 子项目一
  - 子项目二
- 项目三

### 有序列表

```markdown
1. 第一步
2. 第二步
3. 第三步
```

**效果**：
1. 第一步
2. 第二步
3. 第三步

---

## 链接和图片

### 链接

```markdown
[链接文字](https://example.com)
[链接文字](https://example.com "鼠标悬停提示")
```

### 图片

```markdown
! [图片替代文字](image-url.png)
! [图片替代文字](image-url.png "鼠标悬停提示")
```

---

## 代码

### 行内代码

```markdown
使用 `git status` 查看状态
```

**效果**：使用 `git status` 查看状态

### 代码块

````markdown
```python
def hello():
    print("Hello, World!")
```
````

**效果**：
```python
def hello():
    print("Hello, World!")
```

---

## 引用

```markdown
> 这是一段引用
> 可以有多行
```

**效果**：
> 这是一段引用
> 可以有多行

---

## 表格

```markdown
| 列1 | 列2 | 列3 |
|-----|-----|-----|
| 数据1 | 数据2 | 数据3 |
| 数据4 | 数据5 | 数据6 |
```

**效果**：
| 列1 | 列2 | 列3 |
|-----|-----|-----|
| 数据1 | 数据2 | 数据3 |
| 数据4 | 数据5 | 数据6 |

---

## 分隔线

```markdown
---

***

___
```

---

## OpenClaw 中的 Markdown

### Frontmatter（前置元数据）

```markdown
---
title: "文章标题"
date: 2026-03-01
tags: [标签1, 标签2]
category: 分类
---

# 文章内容开始...
```

### Obsidian 特有语法

```markdown
# 双向链接

# 带显示文字的链接

# 嵌入
!

# 标签
#标签名
```

---

## 📝 学习检验

### 问题 1：标题语法

如何创建二级标题？

A. `#二级标题`
B. `## 二级标题`
C. `**二级标题**`

<details>
<summary>点击查看答案</summary>

**答案：B**

解释：Markdown 标题使用 `#` 符号，数量对应级别。 二级标题用两个 `##`，注意 `#` 后需要有空格。

</details>

---

### 问题 2：链接语法

创建一个链接到 `https://openclaw.ai`，显示文字为 "OpenClaw 官网"：

<details>
<summary>点击查看答案</summary>

```markdown
[OpenClaw 官网](https://openclaw.ai)
```

</details>

---

### 问题 3：代码块

如何创建一个 JavaScript 代码块？

<details>
<summary>点击查看答案</summary>

````markdown
```javascript
console.log("Hello, World!");
```
````

</details>

---

### 问题 4：表格创建

创建一个包含"姓名"和"年龄"两列的表格，并添加两行数据。

<details>
<summary>点击查看答案</summary>

```markdown
| 姓名 | 年龄 |
|------|------|
| 张三 | 25 |
| 李四 | 30 |
```

</details>

---

### 问题 5：综合练习

将以下内容用 Markdown 格式编写：

- 一个二级标题："学习笔记"
- 一段包含粗体和斜体的文字
- 一个无序列表，包含三个学习主题
- 一个代码块，显示 `print("Hello")`

<details>
<summary>点击查看答案</summary>

```markdown
## 学习笔记

这是一段**重要的**学习笔记，包含*关键概念*。

### 学习主题

- Python 编程基础
- Git 版本控制
- Markdown 文档编写

\`\`\`python
print("Hello")
\`\`\`
```

</details>

---

## 常见错误

### ❌ 错误示例

```markdown
#标题（缺少空格）
**粗体 *（未闭合）
[链接（缺少右括号）
```

### ✅ 正确示例

```markdown
# 标题
**粗体**
[链接](url)
```

---

## 🔗 相关资源

- [JSON 文件格式入门](2026-03-01-learn-json-format)
- [Git 基础教程](2026-03-01-learn-git-basics)
- [OpenClaw 配置文件说明](2026-03-01-openclaw-config-guide)

---

*OpenClaw 基础技能学习系列*

---
## 📝 翻译说明

本文由 **Azure Translator** 自动翻译。

| 项目 | 信息 |
|------|------|
| **原文** | [Markdown 入门教程](programming/2026-03-01-learn-markdown-basics.md) |
| **翻译服务** | Microsoft Azure Translator |
| **翻译时间** | 2026-03-03 |

> 💬 如发现翻译问题，欢迎在评论区指正。