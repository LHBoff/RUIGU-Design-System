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
├── README.md
├── SKILL.md
├── VERSION
├── CHANGELOG.md
│
└── .agents/
    └── skills/
        └── ruigu-design-system/
            ├── SKILL.md          ← 技能入口（描述能力与规则）
            ├── core/             ← 页面模式 / 组件映射 / Ant Design 规则
            │   ├── ant-design-rules.md
            │   ├── component-mapping.md
            │   └── page-patterns.md
            └── components/       ← 组件参考
                ├── button.md / input.md / select.md / table.md
```

---

## Installation（安装方法）

RUIGU 是一个可被 AI 工具自动发现的 Skill 包，安装 = 把 `ruigu-design-system/` 目录放到目标工具的技能根目录。支持以下任一方式：

### 方式一：GitHub 下载（推荐，先拿到文件）

```bash
git clone https://github.com/LHBoff/RUIGU-Design-System.git
```

克隆后，skill 本体位于 `RUIGU-Design-System/.agents/skills/ruigu-design-system/`。

### 方式二：支持 `.agents/skills/` 约定的 AI 工具（如 Claude Code 等）

把 `ruigu-design-system/` 整个目录复制到目标项目（或工具全局）的 skills 目录下：

```bash
cp -r RUIGU-Design-System/.agents/skills/ruigu-design-system <你的项目>/.agents/skills/
```

工具会自动发现 `SKILL.md`，无需额外配置。

### 方式三：豆包等 AI 平台（个人/团队技能）

将 `ruigu-design-system/` 整个目录放到平台的用户技能根目录，例如豆包：

```bash
cp -r RUIGU-Design-System/.agents/skills/ruigu-design-system ~/.user_skills/ruigu-design-system
```

放置后即被自动识别。最终结构如下：

```text
<技能根目录>/ruigu-design-system/
├── SKILL.md
├── core/
└── components/
```

### 验证安装

在对话中直接提出一个页面需求（如"生成一个带查询区的列表页"），若能按 Ant Design 规范自动生成页面，即安装成功。

---

## Usage（使用方法）

RUIGU 通过自然语言自动识别需求并生成 Ant Design 页面，无需指定组件名。根据是否希望参考上传图片的视觉，有两种模式：

### 默认模式：组件规范优先（无需特殊说明）

直接描述需求即可，页面结构与视觉均按 Ant Design 规范生成：

- "根据这个原型图生成页面"
- "生成一个带查询区的列表页"
- "把这张图做成页面"

### 视觉参考模式：需要参考图片结构与视觉时

在描述中包含指向性词（设计稿 / UI稿 / 设计图 / 高保真 等）：

- "照着这张**设计稿**的样式做"
- "参考这张**UI稿**的结构和配色"
- "按**高保真**视觉还原"

### 切回默认模式

- "用**默认组件样式**，不要参考图片"
- "忽略图片视觉，按 **antd 默认** 实现"

### 两种模式速查

| 模式 | 何时触发 | 图片参考范围 | 产出 |
|---|---|---|---|
| 组件规范优先（默认） | 无指向性词 | 仅内容/功能；结构布局与视觉不参考 | Ant Design 默认结构与样式 |
| 视觉参考 | 含设计稿/UI稿/高保真等 | 结构布局 + 视觉均参考 | 保留图片布局与视觉，组件仍用 Ant Design |

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
Ant Design（按项目实际安装版本，见 SKILL.md 第 7 节）
      ↓
UI / Code
```
