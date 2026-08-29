# RUIGU Input

## Component

Input

## Ant Design Version

Ant Design 4.x

## Official Documentation

https://4x.ant.design/components/input/

---

# 1. Component Identification

Use Input when the user needs to enter, edit, search, or display
text-based information.

Chinese keywords:

- 输入框
- 文本框
- 输入
- 文本输入
- 文字输入
- 名称输入
- 关键词输入
- 搜索框
- 搜索输入框
- 密码输入框
- 多行输入框
- 备注输入框
- 描述输入框

English keywords:

- input
- text input
- text field
- input field
- search input
- search box
- password input
- textarea
- text area
- keyword input
- text field

Chinese-English mixed examples:

- 增加一个 input
- 加一个输入框
- 增加一个 search input
- 做一个搜索框
- 加一个 password input
- 增加一个 textarea

All should be interpreted as Input-related requirements.

---

# 2. Ant Design Mapping

RUIGU Input MUST map to Ant Design 4.x Input components.

Import:

import { Input } from 'antd';

Do not replace Ant Design Input with:

<input>

Do not create a custom Input component when Ant Design
can satisfy the requirement.

---

# 3. Input Variants

Determine the correct Input variant from user intent.

## Standard Input

Use for ordinary single-line text input.

Examples:

- 供应商名称
- 用户姓名
- 商品名称
- 编号
- 地址

Mapping:

<Input />

Example:

<Input placeholder="请输入供应商名称" />

---

## Search Input

Use when the user's intent is searching.

Chinese:

- 搜索
- 查询
- 查找
- 搜索关键词
- 搜索供应商

English:

- search
- find
- query
- search keyword

Mapping:

<Input.Search />

Example:

<Input.Search
  placeholder="请输入供应商名称"
/>

If the design contains a search field with an explicit
search action, prefer Input.Search when appropriate.

---

## Password Input

Use when the user needs to enter a password or secret value.

Examples:

- 密码
- 登录密码
- 确认密码
- password
- confirm password

Mapping:

<Input.Password />

Example:

<Input.Password
  placeholder="请输入密码"
/>

Do not use a normal Input for password entry unless
the requirement explicitly requires plain text.

---

## TextArea

Use when the user needs multiline text.

Examples:

- 备注
- 描述
- 详细说明
- 商品介绍
- 地址详情
- textarea
- multiline input
- long text

Mapping:

<Input.TextArea />

Example:

<Input.TextArea
  rows={4}
  placeholder="请输入备注"
/>

---

# 4. Input Intent Mapping

Use semantic intent rather than only visual appearance.

Examples:

"请输入供应商名称"

→ Text Input

→ Input

---

"搜索供应商"

→ Search

→ Input.Search

---

"请输入密码"

→ Password Input

→ Input.Password

---

"请输入备注"

→ Multiline Text

→ Input.TextArea

---

"请输入关键词并搜索"

→ Search Input

→ Input.Search

---

# 5. Visual Design Mapping

When analyzing a design image:

A rectangular field with text-entry affordance
should normally be considered an Input candidate.

Consider:

- placeholder
- entered value
- prefix icon
- suffix icon
- search icon
- password visibility icon
- clear action
- multiline height
- disabled state
- error state
- required state

Do not determine the component only from its shape.

Use:

1. visual appearance
2. text label
3. interaction intent
4. surrounding UI
5. page context

---

# 6. Prefix and Suffix

If the design contains an icon or text inside
the beginning or end of an input:

Consider Ant Design Input prefix / suffix.

Example:

<Input
  prefix={<SearchOutlined />}
/>

or:

<Input
  suffix=".com"
/>

Do not recreate the input using custom HTML
just to support prefix or suffix content.

---

# 7. Clearable Input

If the design or requirement indicates
that the user can clear the input:

Use the Ant Design allowClear property.

Example:

<Input allowClear />

Do not create a custom clear button
when the Ant Design API can provide the behavior.

---

# 8. Disabled State

If the input cannot currently be edited:

Use:

<Input disabled />

Do not simulate disabled state with CSS alone.

---

# 9. Readonly / Non-editable Content

If the requirement is to display text that looks
like an input but should not be edited:

First determine whether Input is semantically appropriate.

Do not automatically use Input simply because
the visual element is rectangular.

If the element is purely informational,
consider Typography or another appropriate Ant Design component.

---

# 10. Form Integration

When Input is inside a form:

Prefer Ant Design Form + Form.Item.

Example:

<Form.Item
  name="supplierName"
  label="供应商名称"
>
  <Input placeholder="请输入供应商名称" />
</Form.Item>

Do not create custom form validation
when Ant Design Form can satisfy the requirement.

---

# 11. Validation State

When the input is part of a Form,
validation state should normally be handled by
Ant Design Form.Item.

Example:

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

Do not manually recreate Ant Design validation UI
unless there is a specific requirement.

---

# 12. Code Generation Rule

When generating React + TypeScript:

Use:

import { Input } from 'antd';

Examples:

<Input />

<Input.Search />

<Input.Password />

<Input.TextArea />

Never generate:

<input />

<textarea />

when an Ant Design Input component is appropriate.

---

# 13. Chinese / English Recognition

The following should map correctly.

"增加一个输入框"

→ Input

"增加一个 input"

→ Input

"增加一个文本框"

→ Input

"增加一个搜索框"

→ Input.Search

"增加一个 search input"

→ Input.Search

"加一个密码框"

→ Input.Password

"Add a password input"

→ Input.Password

"增加一个 textarea"

→ Input.TextArea

"增加一个多行输入框"

→ Input.TextArea

---

# 14. Validation

Before generating final code verify:

[ ] Correct Input component selected

[ ] Correct Ant Design 4.x API

[ ] Correct variant

[ ] Search uses Input.Search when appropriate

[ ] Password uses Input.Password when appropriate

[ ] Multiline text uses Input.TextArea when appropriate

[ ] Disabled state uses disabled

[ ] Clear behavior uses allowClear when appropriate

[ ] Form validation uses Ant Design Form when appropriate

[ ] No custom Input implementation

[ ] No native input replacement

[ ] No other UI library

---

# 15. Official Source

Use Ant Design 4.x documentation as the authoritative
reference for Input API and behavior.

Official documentation:

https://4x.ant.design/components/input/
