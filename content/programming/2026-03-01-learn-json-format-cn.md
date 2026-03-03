---
title: "JSON 文件格式入门教程 (中文翻译)"
date: 2026-03-01
tags: [programming, 学习教程, openclaw基础技能]
category: programming
lang: zh
learning: true
translation_source: "programming/2026-03-01-learn-json-format"
translator: "Azure Translator"
---

> 🌐 **English Version**: [[programming/2026-03-01-learn-json-format|Read original English version]]

# JSON 文件格式入门教程


# JSON 文件格式入门教程

> 📚 **OpenClaw 基础技能学习** — 本教程帮助你掌握 JSON 文件格式，这是现代编程和数据交换的核心技能。

## 什么是 JSON？

JSON（JavaScript Object Notation）是一种轻量级的数据交换格式。 它易于人类阅读和编写，同时也易于机器解析和生成。

---

## JSON 基本语法

### 1. 对象（Object）

使用花括号 `{}` 表示对象，包含键值对：

```json
{
  "name": "张三",
  "age": 25,
  "city": "北京"
}
```

### 2. 数组（Array）

使用方括号 `[]` 表示数组：

```json
[
  "苹果",
  "香蕉",
  "橙子"
]
```

### 3. 嵌套结构

对象和数组可以互相嵌套：

```json
{
  "name": "李四",
  "hobbies": ["阅读", "游泳", "编程"],
  "address": {
    "city": "上海",
    "district": "浦东新区"
  }
}
```

---

## JSON 数据类型

| 类型 | 示例 | 说明 |
|------|------|------|
| 字符串 | `"Hello"` | 必须使用双引号 |
| 数字 | `42`, `3.14` | 整数或浮点数 |
| 布尔值 | `true`, `false` | 小写 |
| 空值 | `null` | 表示空 |
| 对象 | `{"key": "value"}` | 键值对集合 |
| 数组 | `[1, 2, 3]` | 有序列表 |

---

## 常见错误

### ❌ 错误示例

```json
{
  name: "张三",        // 错误：键必须用双引号
  'age': 25,          // 错误：必须用双引号，不能用单引号
  "price": 99.9,      // 最后一个元素后不能有逗号
}
```

### ✅ 正确示例

```json
{
  "name": "张三",
  "age": 25,
  "price": 99.9
}
```

---

## 实际应用示例

### OpenClaw 配置文件示例

```json
{
  "name": "web-to-knowledge",
  "version": "4.0",
  "features": [
    "网页抓取",
    "内容清理",
    "中文翻译",
    "自动分类"
  ],
  "config": {
    "language": "zh-CN",
    "autoSync": true,
    "maxRetries": 3
  }
}
```

---

## 📝 学习检验

### 问题 1：JSON 基础

下面哪个是有效的 JSON 字符串？

A. `{'name': '张三'}`
B. `{"name": "张三"}`
C. `{name: "张三"}`

<details>
<summary>点击查看答案</summary>

**答案：B**

解释：JSON 键和字符串值必须使用双引号，不能使用单引号或不加引号。

</details>

---

### 问题 2：数据类型判断

以下 JSON 中，`"active"` 的值是什么类型？

```json
{
  "name": "测试用户",
  "active": true,
  "count": 100
}
```

A. 字符串
B. 数字
C. 布尔值

<details>
<summary>点击查看答案</summary>

**答案：C**

解释：`true` 和 `false` 是 JSON 的布尔值类型，不需要引号。

</details>

---

### 问题 3：嵌套结构

请写出表示以下信息的 JSON：

- 书名：《OpenClaw 入门》
- 作者：Zotac
- 标签：教程、编程、AI
- 已完成章节：第1章、第2章

<details>
<summary>点击查看答案</summary>

```json
{
  "书名": "OpenClaw 入门",
  "作者": "Zotac",
  "标签": ["教程", "编程", "AI"],
  "已完成章节": ["第1章", "第2章"]
}
```

</details>

---

### 问题 4：错误修正

找出以下 JSON 的所有错误：

```json
{
  'title': 'JSON教程',
  "chapters": [
    {name: "基础语法"},
    {"name": "进阶用法",}
  ]
}
```

<details>
<summary>点击查看答案</summary>

**错误列表：**

1. `'title'` 应改为 `"title"` — 键必须用双引号
2. `'JSON教程'` 应改为 `"JSON教程"` — 字符串值必须用双引号
3. `name:` 应改为 `"name":` — 键必须用双引号
4. `"进阶用法",` — 数组最后一个元素后不能有逗号

**修正后：**

```json
{
  "title": "JSON教程",
  "chapters": [
    {"name": "基础语法"},
    {"name": "进阶用法"}
  ]
}
```

</details>

---

## 🎯 下一步学习

- [Git 基础教程](2026-03-01-learn-git-basics.md)
- OpenClaw 配置文件详解
- Markdown 格式入门

---

*OpenClaw 基础技能学习系列*


---
## 📝 翻译说明

本文由 **Azure Translator** 自动翻译。

| 项目 | 信息 |
|------|------|
| **原文** | [JSON 文件格式入门教程](programming/2026-03-01-learn-json-format.md) |
| **翻译服务** | Microsoft Azure Translator |
| **翻译时间** | 2026-03-03 |

> 💬 如发现翻译问题，欢迎在评论区指正。
