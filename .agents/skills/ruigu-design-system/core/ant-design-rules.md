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
Validation
↓
Final Output

Do not skip the recognition stages.

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

↓

Final:

Production-oriented UI code.

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
