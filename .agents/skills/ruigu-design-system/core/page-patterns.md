# RUIGU Page Patterns

## Purpose

This file defines page-level patterns for RUIGU Design System.

RUIGU must identify the page type before generating UI code.

The system should understand:

User Requirement
↓
Page Intent
↓
Page Pattern
↓
Page Structure
↓
Component Mapping
↓
Ant Design 4.x
↓
Code

RUIGU should not randomly compose components.

---

# 1. Core Page Patterns

RUIGU supports the following primary page patterns:

1. List Page
2. Detail Page
3. Form Page
4. Dashboard Page

Additional patterns:

5. Search / Result Page
6. Modal Form
7. Empty State Page
8. Login / Authentication Page

---

# 2. Pattern Selection Principle

Determine page pattern based on:

1. User intent
2. Primary task
3. Information structure
4. Interaction model
5. Visual layout

Do not determine page pattern only from the page title.

---

# 3. List Page

## Definition

A List Page is used to display and manage
multiple records.

Typical scenarios:

- 用户管理
- 供应商管理
- 商品管理
- 订单管理
- 客户管理
- 账号管理
- 项目管理
- 数据管理

English:

- user management
- supplier management
- product management
- order management
- customer management
- account management
- project management

---

## Typical Structure

List Page:

Page Header
↓
Search / Filter Area
↓
Action Area
↓
Table
↓
Pagination

Typical layout:

┌────────────────────────────────────┐
│ 页面标题                            │
│ 页面描述                            │
├────────────────────────────────────┤
│ 搜索     状态▼    类型▼    查询      │
├────────────────────────────────────┤
│                         + 新增       │
├────────────────────────────────────┤
│ Table                              │
│                                    │
│ 数据 数据 数据 数据 数据            │
│ 数据 数据 数据 数据 数据            │
│ 数据 数据 数据 数据 数据            │
├────────────────────────────────────┤
│              Pagination             │
└────────────────────────────────────┘

---

## Recommended Components

Page Header:

Typography
Breadcrumb

Search:

Input
Input.Search

Filter:

Select

Actions:

Button

Data:

Table

Pagination:

Pagination
or Table pagination

---

## Example

User:

"创建一个供应商管理页面"

RUIGU should identify:

Page Pattern:

List Page

Components:

Input.Search
Select
Button
Table
Pagination

---

# 4. List Page Recognition

Strong indicators:

- 多条数据
- 表格
- 数据列表
- 搜索
- 筛选
- 查询
- 新增
- 编辑
- 删除
- 分页
- 批量操作

English indicators:

- list
- table
- search
- filter
- query
- create
- edit
- delete
- pagination
- bulk action

When multiple indicators appear together,
strongly consider List Page.

---

# 5. List Page Search Area

Search / Filter area commonly contains:

Input
Select
DatePicker
Button

Example:

[供应商名称________]
[状态 ▼]
[类型 ▼]
[查询]
[重置]

Mapping:

供应商名称
→ Input

状态
→ Select

类型
→ Select

查询
→ Button

重置
→ Button

---

# 6. List Page Action Area

Actions commonly include:

- 新增
- 创建
- 导入
- 导出
- 批量删除

Examples:

[新增供应商]

→ Button type="primary"

[导入]

→ Button

[导出]

→ Button

[批量删除]

→ Button danger

---

# 7. List Page Table

The primary data display component
should normally be:

Table

Possible features:

- row selection
- sorting
- filtering
- status
- row actions
- pagination
- expandable rows

Use Ant Design Table APIs.

---

# 8. Detail Page

## Definition

A Detail Page displays information
about one specific entity.

Examples:

- 用户详情
- 供应商详情
- 商品详情
- 订单详情
- 项目详情

English:

- user detail
- supplier detail
- product detail
- order detail
- project detail

---

## Typical Structure

Page Header
↓
Basic Information
↓
Detailed Information
↓
Related Information
↓
Actions

Example:

┌─────────────────────────────┐
│ ← 供应商详情                 │
├─────────────────────────────┤
│ 基本信息                     │
│                             │
│ 名称：ABC公司                │
│ 联系人：张三                 │
│ 电话：138xxxx               │
│ 状态：启用                   │
├─────────────────────────────┤
│ 其他信息                     │
│                             │
│ 地址：xxxx                  │
│ 描述：xxxx                  │
├─────────────────────────────┤
│                 编辑        │
└─────────────────────────────┘

---

## Recommended Components

Page Header:

Typography
Breadcrumb

Information:

Descriptions

Grouping:

Card

Status:

Tag
Badge

Actions:

Button

---

# 9. Detail Page Recognition

Strong indicators:

- 详情
- 查看详情
- 信息
- 基本信息
- 详细信息
- 返回
- 编辑

English:

- detail
- details
- information
- overview
- profile
- view details

If the primary goal is viewing one entity,
prefer Detail Page.

---

# 10. Form Page

## Definition

A Form Page is used to create or edit
structured information.

Examples:

- 新增供应商
- 编辑供应商
- 创建用户
- 编辑商品
- 新建订单

English:

- create supplier
- edit supplier
- create user
- edit product

---

## Typical Structure

Page Header
↓
Form
↓
Form Fields
↓
Actions

Example:

┌─────────────────────────────┐
│ 新增供应商                   │
├─────────────────────────────┤
│ 供应商名称                  │
│ [________________]          │
│                             │
│ 供应商类型                  │
│ [请选择 ▼]                  │
│                             │
│ 联系人                      │
│ [________________]          │
│                             │
│ 联系电话                    │
│ [________________]          │
│                             │
│              [取消] [保存]   │
└─────────────────────────────┘

---

## Recommended Components

Form:

Form

Field:

Form.Item

Text:

Input

Selection:

Select

Date:

DatePicker

Number:

InputNumber

Upload:

Upload

Actions:

Button

---

# 11. Form Page Recognition

Strong indicators:

- 新增
- 创建
- 编辑
- 修改
- 填写
- 提交
- 保存

English:

- create
- add
- edit
- update
- submit
- save
- form

If the primary goal is collecting structured information,
use Form Page.

---

# 12. Form Validation

Use Ant Design Form validation.

Example:

<Form.Item
  name="name"
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

Do not create custom validation UI
when Ant Design Form supports the requirement.

---

# 13. Dashboard Page

## Definition

Dashboard Page presents
high-level metrics, trends, summaries,
and visual data.

Examples:

- 数据看板
- 工作台
- 运营中心
- 数据中心
- 首页
- 经营概览

English:

- dashboard
- analytics dashboard
- overview
- workspace
- data center

---

## Typical Structure

Page Header
↓
Summary Metrics
↓
Charts / Data Visualization
↓
Tables / Lists

Example:

┌────────┬────────┬────────┬────────┐
│ 用户数  │ 订单数  │ 销售额  │ 转化率  │
├────────┴────────┴────────┴────────┤
│                                    │
│           数据趋势图               │
│                                    │
├────────────────────────────────────┤
│ 最近订单 / 数据列表                │
└────────────────────────────────────┘

---

## Recommended Components

Cards:

Card

Metrics:

Statistic

Status:

Tag
Badge

Data:

Table

Charts:

Use the project's approved chart solution
if one exists.

Do not invent a custom chart library
unless explicitly requested.

---

# 14. Dashboard Recognition

Strong indicators:

- 数据看板
- 数据概览
- 指标
- 趋势
- 统计
- 销售额
- 用户数
- 转化率
- 工作台

English:

- dashboard
- metrics
- analytics
- statistics
- trends
- overview
- KPI

---

# 15. Search / Result Page

## Definition

A Search / Result Page is primarily focused
on searching and displaying search results.

Typical structure:

Search Area
↓
Search Conditions
↓
Result Count
↓
Result List / Table
↓
Pagination

Example:

[搜索关键词________] [搜索]

共 128 条结果

Table

Pagination

---

# 16. Modal Form

## Definition

Use Modal Form when a create/edit interaction
occurs inside a temporary dialog.

Example:

List Page

↓
点击“新增”

↓
Modal

↓
Form

Typical structure:

Button
→ Modal
→ Form
→ Form.Item
→ Input / Select
→ Button

---

# 17. Modal Form Recognition

Indicators:

- 点击新增弹窗
- 弹窗编辑
- 对话框填写
- modal form
- dialog form

Example:

"点击新增供应商后弹出一个表单"

Mapping:

Button
+
Modal
+
Form
+
Input
+
Select

---

# 18. Empty State Page

## Definition

Used when the page has no data
or no content.

Examples:

- 暂无数据
- 暂无记录
- 尚未创建
- No Data
- No Results
- Empty State

Recommended component:

Empty

Possible actions:

Button

Example:

<Empty
  description="暂无供应商"
/>

---

# 19. Login / Authentication Page

## Definition

Used for authentication.

Examples:

- 登录
- 注册
- 忘记密码
- 登录账号

English:

- login
- sign in
- sign up
- forgot password
- authentication

Possible components:

Form
Input
Input.Password
Button

---

# 20. Pattern Composition

Pages can combine patterns.

Example:

Supplier Management

Primary Pattern:

List Page

Secondary Pattern:

Modal Form

Structure:

List Page
+
Modal Form

Example:

Supplier List
↓
Click "新增供应商"
↓
Modal
↓
Form

---

# 21. Detail + Edit

A Detail Page may contain
an edit action.

Example:

Detail Page

↓
[编辑]

↓

Form Page

or:

Modal Form

depending on the design.

---

# 22. Pattern Selection Priority

When multiple patterns are possible:

1. Primary user task
2. Information structure
3. Interaction model
4. Page layout
5. Visual appearance
6. Keywords

Examples:

"供应商管理"

→ List Page

"新增供应商"

→ Form Page

"供应商详情"

→ Detail Page

"供应商管理 + 点击新增弹窗"

→ List Page + Modal Form

---

# 23. Design Image Recognition

When a design image is provided:

Analyze the entire page before identifying components.

Step 1:

Identify page purpose.

Step 2:

Identify major regions.

Step 3:

Identify page pattern.

Step 4:

Identify components inside each region.

Step 5:

Map components to Ant Design 4.x.

Example:

Design image:

Header
↓
Search area
↓
Filter area
↓
Action area
↓
Table
↓
Pagination

RUIGU interpretation:

List Page

Components:

Typography
Input
Select
Button
Table
Pagination

---

# 24. Page Pattern Output

When analyzing a design or requirement,
RUIGU should internally produce:

Page Pattern:

List Page

Page Regions:

1. Page Header
2. Search Area
3. Action Area
4. Data Area
5. Pagination

Components:

Page Header
→ Typography

Search
→ Input.Search

Status
→ Select

Create
→ Button

Data
→ Table

Pagination
→ Pagination

---

# 25. Code Generation

Only generate final code
after the page pattern is identified.

Example:

List Page:

import {
  Button,
  Input,
  Select,
  Table,
} from 'antd';

Then compose the page.

Do not generate components
without first determining
their page-level role.

---

# 26. Validation

Before final output:

[ ] Page pattern identified

[ ] Primary user task identified

[ ] Page regions identified

[ ] Components mapped

[ ] Ant Design 4.x components selected

[ ] Components match the page pattern

[ ] No unnecessary custom components

[ ] No native HTML replacement

[ ] No other UI library

[ ] Code follows RUIGU component mapping

---

# 27. Golden Rule

First understand the page.

Then understand the region.

Then select the component.

Then generate code.

Never:

Image
→ Guess Component
→ Generate Code

Correct process:

Image
→ Page Understanding
→ Pattern Recognition
→ Region Recognition
→ Component Recognition
→ Ant Design Mapping
→ Code
→ Validation
