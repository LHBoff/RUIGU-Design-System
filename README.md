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

`0.2.0`

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

## Visual Mode

RUIGU 默认按组件库规范生成页面，避免被上传图片的视觉和结构干扰：

* 默认（组件规范优先）：上传原型图 / 设计图 / 截图时，图片仅作内容、功能、交互参考。页面结构按 Ant Design 页面模式规范组织（如表格上方查询区一行最多 3 个筛选/输入框），视觉采用 Ant Design 默认样式（默认蓝色、8px 网格、默认排版）；不参考图片的布局排布（如筛选区上下单列、单列布局），也不参考颜色 / 圆角 / 阴影 / 字体。
* 仅当指令或图片上标注包含指向性文案（如"设计稿 / UI稿 / 设计图 / 高保真 / 视觉还原"）时，才进入视觉参考模式，参考图片的结构布局与视觉样式，再结合 Ant Design 组件搭建页面。

如需参考图片布局与视觉，在需求中说明即可，例如"照着这张**设计稿**的样式做"；如需切回默认，说明"用**默认组件样式**"。

## Design Principle

RUIGU does not replace Ant Design.

RUIGU adds an AI decision layer on top of Ant Design.

The decision flow is:

```text
User Requirement
      ↓
Visual Mode Detection（默认 Component-First；含"设计稿/设计图"等 → Visual-Reference）
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
