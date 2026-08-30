# RUIGU-Design-System
RUIGU Design System（锐锢中台组件库）是一套基于 Ant Design 的 AI UI Design System Skill，帮助 AI 理解中英文自然语言需求、选择合适的 UI 组件与页面模式，并辅助生成规范化的 UI 设计与 React + TypeScript 代码。

---

## What can RUIGU do?

### For Designers

你可以直接使用自然语言：

* 增加一个按钮
* 加一个 primary button
* 做一个供应商列表
* 增加一个搜索框
* 做一个 Dashboard
* 帮我检查这个页面是否符合规范

不要求必须使用英文组件名称。

---

### For Developers

可以要求 AI：

* 生成 React + TypeScript + Ant Design 页面
* 根据需求选择组件
* 根据业务语义配置组件
* 检查组件 API
* Review UI implementation
* 修复不符合 Design System 的代码

---

## Language Support

RUIGU 支持：

Chinese

```text
增加一个按钮
增加一个主按钮
增加一个输入框
做一个表格
```

English

```text
Add a button
Add a primary button
Add an input
Create a table
```

Mixed

```text
增加一个 primary button
加一个 search input
做一个 supplier table
增加一个 delete button
```

---

## Technology Standard

Base Design System:

Ant Design

Default development stack:

* React
* TypeScript
* Ant Design

---

## Version

Current version:

`0.1.0`

---

## Repository Structure

```text
RUIGU-Design-System/
│
├── SKILL.md
├── VERSION
├── CHANGELOG.md
├── README.md
│
├── components/
├── patterns/
├── glossary/
└── examples/
```

---

## Update Policy

GitHub is the source of truth.

When the Skill is updated:

1. Modify the source files.
2. Update VERSION.
3. Update CHANGELOG.md.
4. Test the Skill.
5. Commit changes.
6. Create a Release when appropriate.
7. Update the team's shared Skill distribution according to the AI platform being used.

Important:

Updating GitHub does not automatically update independently installed copies unless the AI platform provides a shared Skill synchronization mechanism.

---

## Design Principle

RUIGU does not replace Ant Design.

RUIGU adds an AI decision layer on top of Ant Design.

The decision flow is:

```text
User Requirement
      ↓
Business Intent
      ↓
Page Pattern
      ↓
Component
      ↓
Variant / Props
      ↓
Component Composition
      ↓
Ant Design 4.x
      ↓
UI / Code
```
