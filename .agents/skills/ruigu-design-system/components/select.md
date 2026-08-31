# RUIGU Select

## Component

Select

## Ant Design Version

Ant Design 4.x

## Official Documentation

https://4x.ant.design/components/select/

---

# 1. Component Identification

Use Select when the user needs to choose one or more
options from a predefined list.

Chinese keywords:

- 下拉框
- 下拉选择
- 选择框
- 选择器
- 下拉菜单
- 下拉选项
- 选择
- 筛选条件
- 状态选择
- 类型选择
- 分类选择
- 地区选择
- 单选
- 多选
- 多选框

English keywords:

- select
- dropdown
- dropdown select
- selector
- selection
- dropdown menu
- filter select
- single select
- multi select
- multiple select

Chinese-English mixed examples:

- 增加一个 select
- 加一个下拉框
- 增加一个 dropdown
- 加一个状态 Select
- 做一个 multi select
- 增加一个多选 select

All should be interpreted as Select-related requirements.

---

# 2. Ant Design Mapping

RUIGU Select MUST map to:

antd.Select

Import:

import { Select } from 'antd';

Do not replace Select with:

<select>

Do not create a custom Select component when Ant Design
can satisfy the requirement.

---

# 3. Single Select

Use Select when the user can choose one option.

Examples:

- 状态
- 类型
- 分类
- 地区
- 所属部门
- 供应商类型

Mapping:

<Select />

Example:

<Select
  placeholder="请选择状态"
  options={[
    {
      label: '启用',
      value: 'enabled',
    },
    {
      label: '停用',
      value: 'disabled',
    },
  ]}
/>

---

# 4. Multiple Select

Use mode="multiple" when the user needs to select
multiple independent options.

Chinese:

- 多选
- 可以选择多个
- 选择多个分类
- 多个标签

English:

- multiple select
- multi select
- select multiple options

Mapping:

<Select mode="multiple" />

Example:

<Select
  mode="multiple"
  placeholder="请选择分类"
/>

Do not use multiple selection unless the requirement
or design indicates that multiple values are allowed.

---

# 5. Searchable Select

If the user needs to search options inside the selector:

Use Ant Design Select search capability.

Example:

<Select
  showSearch
  placeholder="请选择供应商"
/>

Typical use cases:

- 供应商选择
- 用户选择
- 城市选择
- 商品选择
- 大量数据选项

Do not build a custom search dropdown
when Ant Design Select can provide the behavior.

---

# 6. Disabled Select

If the selector cannot currently be changed:

Use:

<Select disabled />

Do not simulate the disabled state with CSS alone.

---

# 7. Clearable Select

If the user needs to clear the selected value:

Use:

<Select allowClear />

Do not create a custom clear control
when Ant Design provides the behavior.

---

# 8. Loading Select

If options are loading asynchronously:

Use:

<Select loading />

Do not create custom loading UI
when Ant Design Select can represent the state.

---

# 9. Intent Recognition

Determine Select from semantic intent.

Examples:

"选择供应商状态"

→ Selection

→ Select

---

"选择供应商类型"

→ Selection

→ Select

---

"筛选启用状态"

→ Filter

→ Select

---

"选择多个标签"

→ Multiple Selection

→ Select
→ mode="multiple"

---

"选择供应商，可以搜索"

→ Searchable Selection

→ Select
→ showSearch

---

# 10. Visual Design Mapping

When analyzing a design image,
a field containing a dropdown indicator,
such as:

[ 状态 ▼ ]

should be considered a Select candidate.

However, visual appearance alone is not sufficient.

Also consider:

1. Label
2. Current value
3. Dropdown indicator
4. Interaction behavior
5. Available options
6. Whether multiple values are possible
7. Page context

**Visual Mode（模式前提，见 SKILL.md 第 2 节）：** 视觉外观仅用于辅助判断组件类型，不用于定制最终视觉。默认组件规范优先模式下，Select 呈现 Ant Design 默认样式，不参考图片中的边框 / 圆角 / 背景 / 颜色。

---

# 11. Select vs Input

This distinction is important.

Use Input when:

The user enters free-form text.

Example:

[请输入供应商名称]

→ Input

Use Select when:

The user chooses from predefined options.

Example:

[请选择状态 ▼]

→ Select

Use Input.Search when:

The user enters a keyword to search data.

Example:

[搜索供应商 🔍]

→ Input.Search

---

# 12. Select vs Button

Do not confuse a dropdown selector with a Button.

Example:

[请选择状态 ▼]

→ Select

Example:

[更多操作 ▼]

→ Button + Dropdown/Menu may be more appropriate.

Determine the semantic purpose before selecting the component.

---

# 13. Select inside Form

When Select is used inside a form:

Prefer:

Form
+
Form.Item
+
Select

Example:

<Form.Item
  name="status"
  label="状态"
>
  <Select
    placeholder="请选择状态"
    options={[
      {
        label: '启用',
        value: 'enabled',
      },
      {
        label: '停用',
        value: 'disabled',
      },
    ]}
  />
</Form.Item>

Do not create custom form logic
when Ant Design Form can satisfy the requirement.

---

# 14. Filter Scenario

For management pages,
Select is commonly used as a filter.

Example:

供应商管理

[供应商名称] [状态 ▼] [类型 ▼] [搜索]

Mapping:

供应商名称
→ Input

状态
→ Select

类型
→ Select

搜索
→ Button or Input.Search
depending on the design and interaction.

---

# 15. Chinese / English Recognition

The following should map correctly.

"增加一个下拉框"

→ Select

"增加一个 select"

→ Select

"增加一个 dropdown"

→ Select

"增加一个状态选择器"

→ Select

"增加一个 status select"

→ Select

"增加一个多选框"

→ Select
→ mode="multiple"

"增加一个 multi select"

→ Select
→ mode="multiple"

"增加一个可搜索下拉框"

→ Select
→ showSearch

"Add a searchable select"

→ Select
→ showSearch

---

# 16. Code Generation Rule

When generating React + TypeScript:

Use:

import { Select } from 'antd';

Examples:

<Select />

<Select
  mode="multiple"
/>

<Select
  showSearch
/>

<Select
  allowClear
/>

Never generate:

<select />

when Ant Design Select is appropriate.

---

# 17. Custom Component Rule

Only create a custom selector when
Ant Design Select cannot satisfy the requirement.

If custom behavior is required:

1. Identify the unsupported requirement.
2. Check available Ant Design 4.x APIs.
3. Determine whether Select can be composed with
   other Ant Design components.
4. Only then consider a custom component.

Do not immediately create a custom dropdown.

---

# 18. Validation

Before generating final code verify:

[ ] Correct Select component selected

[ ] Correct Ant Design 4.x API

[ ] Single select vs multiple select is correct

[ ] showSearch is used when appropriate

[ ] allowClear is used when appropriate

[ ] disabled is used when appropriate

[ ] loading is used when appropriate

[ ] Form integration uses Form.Item when appropriate

[ ] No custom Select implementation

[ ] No native select replacement

[ ] No other UI library

---

# 19. Official Source

Use Ant Design 4.x documentation as the authoritative
reference for Select API and behavior.

Official documentation:

https://4x.ant.design/components/select/
