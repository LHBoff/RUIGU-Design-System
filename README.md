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

安装 RUIGU 就像"下载一个文件、解压、把文件夹放到指定位置"一样，**全程不需要写代码、不需要打开命令行**。整个安装分三步：

### 第一步：下载 skill 文件

1. 用浏览器打开仓库页面：**https://github.com/LHBoff/RUIGU-Design-System**
2. 点击页面右侧的绿色 **「Code」** 按钮
3. 在弹出的菜单里点击 **「Download ZIP」**（下载压缩包）
4. 浏览器会下载一个名为 `RUIGU-Design-System-main.zip` 的文件，**双击它解压**（Mac 双击自动解压；Windows 右键 →「全部解压缩」）

### 第二步：找到要安装的 skill 文件夹

解压后，按这个路径一层层进入：
`RUIGU-Design-System-main` → `agents` → `skills`

里面有一个叫 **`ruigu-design-system`** 的文件夹（里面有一个 `SKILL.md` 文件），这就是要安装的 skill 本体。记住它的位置。

### 第三步：把 skill 文件夹放进你的 AI 工具

把这个 `ruigu-design-system` **整个文件夹复制**到你正在使用的 AI 工具对应的位置（如果该位置不存在，就自己新建一个同名文件夹再放进去）：

| 你使用的 AI 工具 | 能否直接安装 | skill 文件/文件夹要放到的位置 |
|---|---|---|
| Claude Code | ✅ 可以 | `~/.claude/skills/ruigu-design-system` |
| Qoder | ✅ 可以 | `~/.qoder/skills/ruigu-design-system` |
| Codex | ✅ 可以 | `~/.codex/skills/ruigu-design-system` |
| 其他支持 `.agents/skills` 的工具 | ✅ 可以 | 项目的 `.agents/skills/ruigu-design-system` |
| Figma Make | ✅ 可以 | 聊天框 → Skills → Add skill → 上传 SKILL.md（需单文件版，见下） |
| 墨刀 AI 客户端 | ✅ 可以 | 官方标注支持 skill 扩展，具体入口以客户端内 Skill 为准 |

> 提示：`~` 表示你电脑的"用户目录"（Windows 一般是 `C:\Users\你的用户名`）。放好文件夹即安装完成，**不需要运行任何命令**。Qoder 放好后重启一次，在对话框输入 `/` 即可看到技能。

> **关于 Figma Make / 墨刀 AI 客户端**：
> - **Figma Make**（及 Figma agent）支持上传自定义 Skill：在聊天框点击 **Skills** → **Add skill** → **Upload a file**，选择 SKILL.md 文件上传即可，之后用 `/技能名` 调用。注意 Figma 要求**单个 Markdown 文件**（不支持 `scripts/`、`references/` 等子目录），因此需要 RUIGU 的**单文件版**（把 `core/`、`components/` 内容合并进一个 SKILL.md）。
> - **墨刀 AI 客户端**（桌面端）官方标注"支持 skill 扩展和定时任务"，可在墨刀官网下载客户端后，在客户端内添加 Skill（具体入口以客户端内实际界面为准）。

### 验证是否装好

重新打开你的 AI 工具，在对话里直接说一个需求，例如："**生成一个带查询区的列表页**"。如果它能按 Ant Design 规范自动生成页面，就说明安装成功。

### 开发者快捷方式（可选，会用命令行才用）

如果你会用命令行，也可以跳过第一步，直接用下面这行命令把整个仓库下载到当前文件夹（效果等同"下载 ZIP"）：

```bash
git clone https://github.com/LHBoff/RUIGU-Design-System.git
```

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
