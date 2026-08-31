# RUIGU Component Mapping

## Purpose

This file defines the component decision system of
RUIGU Design System.

The purpose is NOT simply to match keywords.

The purpose is to understand the user's intent,
identify the UI element,
select the appropriate Ant Design 4.x component,
and generate a standardized implementation.

Decision flow:

User Input
↓
Intent Recognition
↓
UI Element Recognition
↓
Component Selection
↓
Ant Design 4.x Mapping
↓
Implementation

---

# 1. Core Principle

RUIGU must not blindly map words to components.

RUIGU must understand:

- what the user wants to do
- what information the user needs to provide
- what information the system needs to display
- what interaction is required
- whether the interaction is single-select or multi-select
- whether the content is structured data
- whether the action is destructive
- whether the element is part of a form
- whether the element is part of a management page

Semantic intent has higher priority than literal keywords.

**Visual Mode（模式前提，见 SKILL.md 第 2、12 节）：** 组件识别始终基于语义目的、交互、内容、上下文与状态，**不基于外观**。默认组件规范优先模式下，图片的视觉（颜色、圆角、阴影等）不参与组件选择，也不参与最终视觉定制；图片的结构布局（上下/左右、单列、分组等）不参与页面组织——结构与视觉均按 Ant Design 默认规范实现。仅当指令含"设计稿/设计图/高保真"等指向性文案（视觉参考模式）时，图片的布局与视觉才影响实现。

---

# 2. Component Decision Matrix

| User Intent | Chinese Examples | English Examples | Component |
|---|---|---|---|
| Trigger action | 按钮、提交、新增、保存 | button, submit, create | Button |
| Enter text | 输入框、名称、关键词 | input, text field | Input |
| Search | 搜索、查询、查找 | search, query | Input.Search |
| Choose one | 下拉框、状态选择 | select, dropdown | Select |
| Choose multiple | 多选、多选标签 | multi select | Select mode="multiple" |
| Display structured records | 表格、数据表 | table, data table | Table |
| Confirm destructive action | 删除确认 | delete confirmation | Popconfirm / Modal |
| Show temporary dialog | 弹窗、对话框 | modal, dialog | Modal |
| Display status | 状态标签 | status, tag | Tag / Badge |
| Navigate pages | 分页 | pagination | Pagination |
| Display grouped content | 卡片 | card | Card |
| Submit structured data | 表单 | form | Form |
| Display empty state | 暂无数据 | empty state | Empty |

---

# 3. Button Decision

Use Button when the user wants to trigger an action.

Examples:

"新增供应商"

→ Button

"保存"

→ Button

"提交"

→ Button

"删除"

→ Button

"取消"

→ Button

"Add button"

→ Button

"Primary action"

→ Button

---

# 4. Button Type Decision

Determine Button type based on semantic importance.

Primary action:

- 新增
- 创建
- 保存
- 提交
- 确定

→ Button type="primary"

Destructive:

- 删除
- 移除
- 清空
- 停用
- 作废

→ Button danger

Secondary:

- 取消
- 返回

→ Button

Low emphasis:

- 编辑
- 查看
- 详情

→ Button type="text" or type="link"
depending on visual design and context.

---

# 5. Input Decision

Use Input when the user enters free-form text.

Examples:

"请输入供应商名称"

→ Input

"输入用户名"

→ Input

"请输入编号"

→ Input

"Add an input"

→ Input

"增加一个 text field"

→ Input

---

# 6. Search Decision

Use Input.Search when the user enters a keyword
specifically to search or query.

Examples:

"搜索供应商"

→ Input.Search

"查询订单"

→ Input.Search

"Search users"

→ Input.Search

"搜索关键词"

→ Input.Search

Important:

Do not use Input.Search simply because
an input contains a search icon.

Determine whether the interaction actually represents
a search operation.

---

# 7. Select Decision

Use Select when the user chooses from predefined options.

Examples:

"选择状态"

→ Select

"选择供应商类型"

→ Select

"请选择地区"

→ Select

"Select status"

→ Select

"Dropdown"

→ Select

---

# 8. Multiple Select Decision

Use:

Select mode="multiple"

when multiple independent values can be selected.

Examples:

"选择多个标签"

→ Select mode="multiple"

"多选分类"

→ Select mode="multiple"

"Multi select"

→ Select mode="multiple"

"Select multiple categories"

→ Select mode="multiple"

Do not use multiple mode for ordinary single-choice fields.

---

# 9. Searchable Select Decision

Use:

Select showSearch

when the user chooses from predefined options
and needs to search those options.

Examples:

"可搜索供应商"

→ Select showSearch

"搜索并选择供应商"

→ Select showSearch

"Searchable dropdown"

→ Select showSearch

Important distinction:

Search data:

→ Input.Search

Search options inside selector:

→ Select showSearch

---

# 10. Table Decision

Use Table when information is structured
into rows and columns.

Examples:

"供应商列表"

if columns exist:

供应商名称
联系人
电话
状态
操作

→ Table

"用户管理列表"

if records contain multiple structured fields:

→ Table

"订单数据表"

→ Table

"Data table"

→ Table

---

# 11. List vs Table

Do not automatically map every "列表"
to Table.

Use Table when:

- multiple columns exist
- records share a consistent structure
- users compare fields across records
- column headers exist

Use List when:

- items are primarily independent content
- there are no meaningful columns
- the interface behaves like a feed

Example:

供应商名称 | 联系人 | 状态

→ Table

Example:

通知中心

- 系统通知
- 审核提醒
- 消息提醒

→ List

---

# 12. Input vs Select

This is one of the most important decisions.

Ask:

Can the user enter arbitrary text?

YES

→ Input

Can the user only choose predefined options?

YES

→ Select

Example:

供应商名称:

[请输入供应商名称]

→ Input

供应商状态:

[请选择 ▼]

→ Select

---

# 13. Input.Search vs Select

Ask:

Is the user searching the database?

YES

→ Input.Search

Is the user searching options inside a selector?

YES

→ Select showSearch

Example:

[搜索供应商]

→ Input.Search

Example:

[选择供应商 ▼]
with searchable options

→ Select showSearch

---

# 14. Button vs Select

Example:

[请选择状态 ▼]

→ Select

Example:

[更多操作 ▼]

→ Button + Dropdown/Menu

Reason:

"状态" is a value selection.

"更多操作" is an action selection.

Semantic intent determines the component.

---

# 15. Table vs Card

Use Table when:

users compare multiple records
across consistent fields.

Use Card when:

each item is an independent content block.

Example:

供应商 | 联系人 | 电话 | 状态

→ Table

Example:

┌─────────────┐
│ 供应商名称    │
│ 联系人        │
│ 联系电话      │
│ 描述          │
└─────────────┘

→ Card

---

# 16. Status Recognition

When the design contains:

- 启用
- 停用
- 正常
- 异常
- 处理中
- 已完成
- 失败
- 待审核

consider:

Tag

or:

Badge

depending on the visual representation.

Example:

启用

→ Tag

处理中

→ Badge

Do not create custom status components
without first checking Ant Design components.

---

# 17. Destructive Action

If the user requests:

- 删除
- 移除
- 清空
- 永久删除
- 停用
- 作废

recognize the action as destructive.

Possible structure:

Button danger

and, when confirmation is required:

Popconfirm

or:

Modal

Example:

<Button danger>
  删除
</Button>

Potential confirmation:

<Popconfirm
  title="确定删除吗？"
>
  <Button danger>
    删除
  </Button>
</Popconfirm>

---

# 18. Form Recognition

If the page asks the user to provide
multiple pieces of structured information:

consider Form.

Example:

新增供应商

供应商名称
[Input]

供应商类型
[Select]

联系人
[Input]

联系电话
[Input]

[取消] [保存]

→ Form

Likely components:

Form
Form.Item
Input
Select
Button

---

# 19. Management Page Recognition

When the user requests:

- 用户管理
- 供应商管理
- 商品管理
- 订单管理
- 客户管理
- 账号管理

consider a management page pattern.

Typical structure:

Page Header
↓
Search / Filter
↓
Action Area
↓
Table
↓
Pagination

Potential components:

Input
Input.Search
Select
Button
Table
Pagination

---

# 20. Detail Page Recognition

When the user requests:

- 查看详情
- 详情页
- 用户详情
- 订单详情
- 供应商详情

consider:

Descriptions

Card

Typography

Tag

Button

depending on the visual structure.

Do not automatically use Table
for detail information.

---

# 21. Modal Recognition

Use Modal when the user needs
a temporary dialog or focused interaction.

Keywords:

- 弹窗
- 模态框
- 对话框
- dialog
- modal
- popup dialog

Example:

"点击新增后弹出表单"

→ Button
+
Modal
+
Form

---

# 22. Pagination Recognition

Keywords:

- 分页
- 下一页
- 上一页
- page
- pagination
- page number

→ Pagination

For a Table:

prefer Ant Design Table pagination
when pagination belongs directly to the table.

Use standalone Pagination
when the pagination is independently positioned.

---

# 23. Image / Design Recognition

When a UI image is provided,
RUIGU should not rely on OCR alone.

Analyze:

1. Layout
2. Visual hierarchy
3. Interaction affordances
4. Labels
5. Icons
6. Controls
7. Repeated structures
8. Data density
9. Page context

Then identify components.

Example:

Visual:

[供应商名称________]
[状态 ▼]
[查询] [新增供应商]

↓

Component identification:

Input
Select
Button
Button

**Visual Mode（模式前提，见 SKILL.md 第 2 节）：** 图片分析用于识别组件类型与页面结构；识别依据是语义 / 功能 / 交互 / 上下文，不是外观照抄。默认组件规范优先模式下，图片中的颜色、圆角、阴影等视觉不进入最终实现，一律使用 Ant Design 默认样式。

---

# 24. Component Selection Priority

When multiple components seem possible,
use this priority:

1. Semantic intent
2. Interaction behavior
3. Data type
4. Page pattern
5. Visual appearance
6. User terminology

Never select a component
only because a keyword appears.

---

# 25. Unknown Component

If the user asks for something that does not clearly
map to an existing component:

Do NOT immediately invent a custom component.

First:

1. Analyze the requirement.
2. Check existing Ant Design 4.x components.
3. Check whether multiple Ant Design components
   can be composed.
4. Only then classify as CUSTOM COMPONENT.

---

# 26. Custom Component Declaration

If a custom component is truly necessary,
explicitly declare:

CUSTOM COMPONENT

Then explain:

- requirement
- why existing Ant Design components are insufficient
- proposed composition
- reusable API

Do not silently create custom UI.

---

# 27. Final Component Mapping

Before generating code,
RUIGU should internally produce a mapping similar to:

User requirement:

"做一个供应商管理页面"

↓

Page Pattern:

Management / List

↓

Components:

Search area
→ Input.Search

Status filter
→ Select

Type filter
→ Select

Create action
→ Button type="primary"

Data display
→ Table

Pagination
→ Table pagination or Pagination

↓

Ant Design:

Input.Search
Select
Button
Table
Pagination

---

# 28. Code Rule

After component identification,
generated code MUST use the mapped Ant Design components.

Example:

import {
  Button,
  Input,
  Select,
  Table,
} from 'antd';

Do not bypass the mapping stage.

---

# 29. Final Validation

Before final output:

[ ] User intent identified

[ ] Page pattern identified

[ ] Components identified

[ ] Ant Design 4.x components selected

[ ] Correct variants selected

[ ] No unnecessary custom components

[ ] No native HTML replacement

[ ] No other UI library

[ ] Code matches component mapping

---

# 30. Golden Rule

RUIGU is a decision system,
not a keyword replacement system.

The correct process is:

Understand
→ Identify
→ Decide
→ Map
→ Implement
→ Validate

Never:

Keyword
→ Random Component
→ Code
