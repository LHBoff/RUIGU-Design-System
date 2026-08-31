# RUIGU Design System — Design to Code

## Purpose

Convert:

Design Image / Figma / Prototype / Screenshot / Natural Language

into:

Ant Design 4.x based React + TypeScript UI code.

The goal is not to reproduce visual pixels using arbitrary HTML/CSS.

The goal is to understand the design intent and implement it
using the correct Ant Design 4.x components and patterns.

---

# 1. Execution Pipeline

Always follow this pipeline:

Input
↓
Visual Mode Detection（SKILL.md 第 2 节）
  ├─ 默认：Component-First Mode（组件规范优先，忽略图片视觉）
  └─ 含"设计稿/设计图/高保真"等指向性文案：Visual-Reference Mode（才参考图片视觉）
↓
Design Understanding
↓
Page Pattern Recognition
↓
Layout Region Recognition
↓
Interaction Recognition
↓
Component Recognition
↓
RUIGU Component Mapping
↓
Ant Design 4.x Component Selection
↓
Ant Design API Implementation
↓
React + TypeScript Code
↓
Validation（含 Mode validation 模式一致性验证）
↓
Final Output

Do not skip the recognition stages.

Visual Mode 判定是整个流程的 Step 0，其结论决定后续所有视觉决策：默认模式下图片视觉不参与实现，视觉定制一律禁止；仅视觉参考模式下才允许按图片定制。

---

# 2. Input Types

RUIGU can process:

- natural language
- Chinese requirements
- English requirements
- mixed Chinese / English requirements
- screenshots
- UI design images
- prototypes
- Figma designs
- existing UI code

Examples:

"增加一个按钮"

"Add a button"

"新增供应商"

"Add supplier button"

"这里放一个搜索框"

"Add a search input"

All should be interpreted semantically.

Do not rely only on exact keywords.

**Visual Mode（模式前提，见 SKILL.md 第 2 节）：**

- 无论输入是截图、UI 设计图、原型还是 Figma 设计，**默认组件规范优先**：图片只提供结构 / 内容 / 功能 / 交互 / 层级，视觉（颜色、字体、圆角、阴影、间距、图标风格等）一律忽略，页面用 Ant Design 默认规范实现。
- **仅当输入指令含"设计稿 / 设计图 / 高保真 / 视觉还原"等指向性文案时**，才进入视觉参考模式，图片视觉才参与定制。
- 组件类型与交互始终按语义理解，不按图片外观照抄。

---

# 3. Design Understanding

When a design image is provided,
analyze the complete page before generating code.

Analyze:

1. page purpose
2. page hierarchy
3. major regions
4. information density
5. interaction relationships
6. visual hierarchy
7. component candidates

Do not immediately convert every visible rectangle
into a custom HTML element.

**Visual Mode（模式前提）：** 以上分析用于理解**结构与功能**。在默认的组件规范优先模式下，`visual hierarchy` 仅用于确定布局层级（如哪部分更重要、放前面），**不**转化为颜色 / 字号 / 圆角 / 阴影等视觉定制——最终视觉一律用 Ant Design 默认规范。

---

# 4. Page Recognition

Identify the primary page pattern.

Possible patterns:

- List Page
- Detail Page
- Form Page
- Dashboard Page
- Search / Result Page
- Modal Form
- Empty State
- Login / Authentication

Refer to:

core/page-patterns.md

The primary page pattern should determine
the initial component structure.

---

# 5. Region Recognition

Divide the page into meaningful UI regions.

Common regions:

- Page Header
- Breadcrumb
- Search Area
- Filter Area
- Action Area
- Content Area
- Data Area
- Detail Area
- Form Area
- Footer Actions
- Sidebar
- Modal
- Drawer

Do not create a separate component
for every visual rectangle.

Create regions based on semantic purpose.

---

# 6. Interaction Recognition

Identify what the user can do.

Common interactions:

- search
- filter
- create
- edit
- delete
- submit
- cancel
- reset
- select
- upload
- download
- navigate
- expand
- collapse
- pagination
- sort
- batch operation

Interaction intent is more important
than visual appearance alone.

---

# 7. Component Recognition

For each region,
identify the most appropriate Ant Design component.

Examples:

Search input
→ Input.Search

Text input
→ Input

Password input
→ Input.Password

Multiline text
→ Input.TextArea

Single selection
→ Select

Multiple selection
→ Select mode="multiple"

Date selection
→ DatePicker

Data table
→ Table

Pagination
→ Pagination

Primary action
→ Button type="primary"

Destructive action
→ Button danger

Low-emphasis action
→ Button type="text"

Navigation-like action
→ Button type="link"

Grouped information
→ Card

Structured information
→ Descriptions

Status
→ Tag / Badge

Temporary confirmation
→ Modal / Popconfirm

Empty content
→ Empty

Loading content
→ Spin / Skeleton

Notifications
→ notification / message

---

# 8. Component Selection Priority

When multiple Ant Design components
could represent the same visual element:

1. semantic intent
2. interaction behavior
3. information structure
4. accessibility
5. Ant Design standard pattern
6. visual similarity

Do not choose a component
only because it looks visually similar.

Example:

A blue text element that navigates
should not automatically become:

<Button type="primary">

If it represents low-emphasis navigation,
consider:

<Button type="link">

---

# 9. Existing Component First

Before creating custom UI:

1. Check whether Ant Design 4.x provides
   an appropriate component.

2. Check whether multiple Ant Design components
   can be composed to satisfy the design.

3. Only create a custom component
   when Ant Design cannot reasonably satisfy
   the requirement.

Priority:

Ant Design Component
>
Ant Design Composition
>
Custom Component

---

# 10. Design-to-Component Mapping

Create a semantic mapping before writing code.

Example:

Design:

"供应商管理"

Interpretation:

Page Pattern:
List Page

Regions:

Page Header
Search Area
Action Area
Table Area

Components:

Page Header
→ Typography

Supplier Name
→ Input

Status
→ Select

Search
→ Button

Reset
→ Button

Create Supplier
→ Button type="primary"

Data
→ Table

Pagination
→ Table pagination / Pagination

---

# 11. Component API Selection

After selecting a component,
use the official Ant Design 4.x API.

Do not invent props.

Do not copy visual styles
into arbitrary custom CSS
when an Ant Design API exists.

Example:

Primary button:

<Button type="primary">
  新增
</Button>

Danger button:

<Button danger>
  删除
</Button>

Disabled button:

<Button disabled>
  保存
</Button>

Loading button:

<Button loading>
  保存
</Button>

Multiple Select:

<Select mode="multiple" />

---

# 12. Ant Design Version

Target:

Ant Design 4.x

Do not use APIs introduced only in Ant Design 5.x.

When implementing code,
prefer APIs documented by the Ant Design 4.x documentation.

Official documentation:

https://4x.ant.design/

---

# 13. React Code Generation

Default implementation:

React + TypeScript

Example:

import React from 'react';
import {
  Button,
  Input,
  Select,
  Table,
} from 'antd';

Use functional components.

Example:

const SupplierList: React.FC = () => {
  return (
    <div>
      ...
    </div>
  );
};

export default SupplierList;

---

# 14. Component Imports

Import components from:

antd

Example:

import {
  Button,
  Input,
  Select,
  Table,
} from 'antd';

Do not import equivalent components
from another UI library.

---

# 15. Icons

Prefer:

@ant-design/icons

when an Ant Design icon satisfies the requirement.

Example:

import {
  PlusOutlined,
  SearchOutlined,
  EditOutlined,
  DeleteOutlined,
} from '@ant-design/icons';

Use icons semantically.

Examples:

新增
→ PlusOutlined

搜索
→ SearchOutlined

编辑
→ EditOutlined

删除
→ DeleteOutlined

---

# 16. Layout

Prefer Ant Design layout components
when appropriate.

Examples:

Row
Col
Space
Flex-compatible project utilities

Do not use large amounts of arbitrary
absolute positioning to reproduce a screenshot.

The generated page should remain responsive
and structurally maintainable.

---

# 17. Form Generation

For structured user input,
prefer:

Form
+
Form.Item

Example:

<Form>
  <Form.Item
    name="supplierName"
    label="供应商名称"
    rules={[
      {
        required: true,
        message: '请输入供应商名称',
      },
    ]}
  >
    <Input />
  </Form.Item>
</Form>

Do not manually reproduce
Form validation UI when Ant Design Form
can provide the behavior.

---

# 18. Table Generation

For structured tabular data,
prefer:

Table

Example:

<Table
  columns={columns}
  dataSource={dataSource}
  rowKey="id"
/>

When the design requires:

pagination
→ use Table pagination

selection
→ use rowSelection

sorting
→ use sorter

filters
→ use filters

Do not recreate table behavior
using manually constructed div elements.

---

# 19. Search Form

For list pages,
search and filter controls
should normally be grouped semantically.

Example:

<Form layout="inline">
  <Form.Item label="供应商名称">
    <Input placeholder="请输入供应商名称" />
  </Form.Item>

  <Form.Item label="状态">
    <Select
      placeholder="请选择状态"
    />
  </Form.Item>

  <Form.Item>
    <Button type="primary">
      查询
    </Button>
  </Form.Item>
</Form>

---

# 20. Action Hierarchy

Identify the primary action.

Example:

[新增] [导入] [导出]

Usually:

新增
→ primary

导入
→ default

导出
→ default

Do not make every action
a primary button.

---

# 21. Destructive Actions

For:

删除
移除
停用
清空
作废

prefer:

<Button danger>

When confirmation is appropriate:

Popconfirm

or:

Modal

---

# 22. Responsive Behavior

When generating responsive UI,
do not assume the screenshot
is the only required viewport.

Consider:

- desktop
- tablet
- mobile

Use Ant Design layout mechanisms
where appropriate.

Do not hardcode absolute coordinates
from the design image.

---

# 23. Visual Fidelity

Visual fidelity matters,
but structural correctness has priority.

Priority:

1. Correct component
2. Correct interaction
3. Correct hierarchy
4. Correct content
5. Correct layout
6. Correct spacing
7. Correct typography
8. Visual details

Do not replace an Ant Design component
with a custom implementation
only to achieve minor visual differences.

**Visual Mode（模式前提）：** "视觉保真"的对照目标取决于当前模式（见 SKILL.md 第 2 节）——组件规范优先模式下，目标是与 **Ant Design 默认规范**一致，而非与图片一致；仅视觉参考模式下才以图片视觉为保真目标。

---

# 24. Custom CSS

Custom CSS is allowed for:

- layout adjustments
- spacing
- typography
- responsive behavior
- project-specific visual identity

Custom CSS must not recreate
an existing Ant Design component.

Incorrect:

.custom-button {
  ...
}

when the element should simply be:

<Button />

Correct:

<Button type="primary">
  新增
</Button>

with limited project-specific styling
only when necessary.

**Visual Mode（模式前提）：** 默认组件规范优先模式下，禁止为匹配图片视觉而使用 Custom CSS / 主题定制（不得自定义颜色、圆角、阴影、背景、字体）。仅在视觉参考模式下，且图片明确展示差异时，才可通过 Ant Design 官方 Token / 官方 prop 定制。

---

# 25. Custom Components

A custom component is allowed
only when:

1. no suitable Ant Design component exists
2. Ant Design composition cannot reasonably solve it
3. the custom behavior is genuinely project-specific

When creating a custom component,
reuse Ant Design components internally whenever possible.

Example:

Custom SupplierStatus

may internally use:

Tag

Do not rebuild Tag from scratch.

---

# 26. Existing Project Code

If existing project code is provided:

First inspect:

- package.json
- installed Ant Design version
- project structure
- existing components
- existing design tokens
- existing layout system

Then generate code compatible
with the existing project.

Do not blindly replace
the project's architecture.

---

# 27. Code Quality

Generated code should:

- be readable
- be maintainable
- use semantic names
- avoid unnecessary duplication
- avoid unnecessary abstraction
- use TypeScript types
- use React best practices
- keep component responsibilities clear

Do not create excessive component abstraction
for simple UI.

---

# 28. Final Validation

Before returning code,
perform the following validation.

## Page

[ ] Correct page pattern

[ ] Correct page hierarchy

[ ] Correct major regions

## Components

[ ] Correct Ant Design component

[ ] Component matches semantic intent

[ ] No unnecessary custom components

[ ] No alternative UI library

## API

[ ] Ant Design 4.x API

[ ] No invented props

[ ] No Ant Design 5-only API

[ ] Correct component states

## Code

[ ] React

[ ] TypeScript

[ ] Correct imports

[ ] No unnecessary native HTML controls

[ ] No excessive absolute positioning

[ ] Responsive structure where appropriate

## Design

[ ] Main layout preserved

[ ] Information hierarchy preserved

[ ] Primary actions preserved

[ ] Important visual states preserved

## Visual Mode（模式一致性验证，见 SKILL.md 第 2 节）

组件规范优先模式（默认）：

[ ] 无图片视觉残留（非默认颜色 / 自定义圆角阴影 / 硬编码色值）

[ ] 未因图片视觉添加 ConfigProvider 主题 / colorPrimary 覆盖

[ ] 视觉与 Ant Design 默认规范一致

视觉参考模式（含"设计稿/设计图"等触发词）：

[ ] 每个视觉定制有明确图片依据

[ ] 视觉定制经官方 Token / 官方 prop 实现（非裸 CSS 硬编码）

[ ] 仍以 Ant Design 组件为基础（未换成自定义组件）

---

# 29. Final Output

When the user asks for code,
return:

1. brief implementation summary
2. component mapping
3. complete code
4. implementation notes only when necessary

Do not return long explanations
when the user only asks for code.

---

# 30. Standard Execution Example

User:

"根据这个设计稿生成供应商管理页面"

Visual Mode 判定（SKILL.md 第 2 节）：
指令含"设计稿"→ **Visual-Reference Mode**（可参考图片视觉）

RUIGU should reason:

Input:
Design Image

↓

Page Pattern:
List Page

↓

Regions:

Header
Search
Actions
Table

↓

Components:

Typography
Input
Select
Button
Table

↓

Ant Design:

Input
Select
Button
Table

↓

Code:

React + TypeScript
+
Ant Design 4.x

↓

Validation:

Check component usage
Check API
Check imports
Check page structure
Check mode consistency（视觉参考模式 → 视觉定制须有图片依据、经官方 Token 实现）

↓

Final:

Production-oriented UI code.

---

对照示例（默认模式）——User:

"根据这个原型图 / 截图生成供应商管理页面"（或"把这张图做成页面"）

Visual Mode 判定：
指令无"设计稿/设计图/高保真"等触发词 → **Component-First Mode**（默认）

RUIGU should reason:

Input:
Prototype / Screenshot（仅作结构与内容参考）

↓

Page Pattern / Regions / Components / Ant Design
→ 同上

↓

视觉实现：
一律 Ant Design 默认样式（默认蓝色主色、8px 网格间距、默认排版/圆角/阴影）
忽略原型图中的颜色、圆角、阴影、字体等视觉；不加 ConfigProvider 主题、不自定义颜色

↓

Validation:

Check component usage
Check API
Check imports
Check page structure
Check mode consistency（组件规范优先 → 无图片视觉残留）

↓

Final:

Production-oriented UI code（Ant Design 默认规范）.

---

# 31. Natural Language Recognition

Chinese and English are equivalent
when they express the same intent.

Examples:

增加按钮
→ Button

增加一个button
→ Button

新增按钮
→ Button

Add button
→ Button

添加输入框
→ Input

Add input
→ Input

选择框
→ Select

Dropdown
→ Select

下拉选择
→ Select

数据表格
→ Table

Data table
→ Table

供应商列表
→ List Page + Table

Supplier list
→ List Page + Table

新增供应商
→ Form Page

Create supplier
→ Form Page

供应商详情
→ Detail Page

Supplier detail
→ Detail Page

---

# 32. Do Not Hallucinate

If the design or requirement
does not provide enough information:

Do not invent business logic.

Do not invent data fields.

Do not invent workflows.

Do not invent APIs.

Do not invent component properties.

Use reasonable placeholders
only when required for a functional example.

Clearly distinguish:

design-derived information

from:

implementation assumptions.

---

# 33. Core Principle

RUIGU is a design interpretation
and implementation system.

It should translate:

Human Intent
+
Design
+
Ant Design 4.x

into:

Consistent UI
+
Consistent Components
+
Consistent Code

The fundamental rule is:

Understand first.

Map second.

Implement third.

Validate last.

**Visual Mode First（最高优先级）：** 默认组件规范优先——图片视觉不参与实现，仅当指令含"设计稿/设计图/高保真"等指向性文案时才参考图片视觉（判定见 SKILL.md 第 2 节）。
