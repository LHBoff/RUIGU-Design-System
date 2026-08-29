# RUIGU Button API Specification

## Authority

This specification is based on:

Ant Design 4.x Button

Official documentation:

https://4x.ant.design/components/button-cn/

Current official 4.x documentation version:

4.24.16

Ant Design documentation is the authoritative source.

RUIGU must not invent Button APIs that do not exist
in Ant Design 4.x.

---

# 1. Component

Component:

Button

Import:

import { Button } from 'antd';

---

# 2. Basic Syntax

Default:

<Button>按钮</Button>

Primary:

<Button type="primary">
  新增
</Button>

Default:

<Button>
  取消
</Button>

Dashed:

<Button type="dashed">
  添加
</Button>

Text:

<Button type="text">
  更多
</Button>

Link:

<Button type="link">
  查看详情
</Button>

---

# 3. Button Type

Ant Design 4.x supports:

type="primary"

type="default"

type="dashed"

type="text"

type="link"

Default value:

type="default"

---

# 4. Semantic Mapping

Use:

type="primary"

for the primary action.

Examples:

- 新增
- 创建
- 保存
- 提交
- 确定

Example:

<Button type="primary">
  新增供应商
</Button>

---

Use:

type="default"

for normal secondary actions.

Examples:

- 取消
- 返回
- 重置
- 普通操作

Example:

<Button>
  取消
</Button>

---

Use:

type="dashed"

for add-style actions when the design
specifically indicates a dashed button.

Example:

<Button type="dashed">
  添加
</Button>

Do not use dashed only because
the action means "add".

The visual design must support dashed styling.

---

Use:

type="text"

for low-emphasis actions.

Examples:

- 更多
- 操作
- 次级操作

Example:

<Button type="text">
  更多
</Button>

---

Use:

type="link"

for navigation-like or low-emphasis
inline actions.

Examples:

- 查看详情
- 查看
- 跳转
- 详情

Example:

<Button type="link">
  查看详情
</Button>

---

# 5. Primary Button Rule

Within one action area:

Prefer only ONE primary button.

Example:

Correct:

<Button type="primary">
  新增
</Button>

<Button>
  导入
</Button>

<Button>
  导出
</Button>

Incorrect:

<Button type="primary">
  新增
</Button>

<Button type="primary">
  导入
</Button>

<Button type="primary">
  导出
</Button>

Reason:

Ant Design recommends one primary action
within an action area.

---

# 6. Button Size

Ant Design 4.x supports:

size="large"

size="middle"

size="small"

Default:

size="middle"

Example:

<Button
  type="primary"
  size="large"
>
  保存
</Button>

Example:

<Button
  size="small"
>
  编辑
</Button>

---

# 7. Size Recognition

When analyzing a design:

Large:

Use when the button is visually prominent
and the surrounding design clearly indicates
large controls.

Middle:

Default choice.

Small:

Use for compact interfaces,
table actions,
dense toolbars,
or when the design clearly shows
a smaller control.

Do not arbitrarily use small
just to make the page more compact.

---

# 8. Danger

Ant Design 4.x uses:

danger

as a property.

Example:

<Button danger>
  删除
</Button>

Do NOT use:

type="danger"

because danger is a property in Ant Design 4.x.

---

# 9. Destructive Action

Typical destructive actions:

- 删除
- 移除
- 清空
- 停用
- 作废
- 取消订单

Use:

<Button danger>
  删除
</Button>

When confirmation is required,
consider:

Popconfirm

or:

Modal

Example:

<Popconfirm
  title="确定删除吗？"
>
  <Button danger>
    删除
  </Button>
</Popconfirm>

---

# 10. Disabled

Use:

disabled

Example:

<Button
  disabled
>
  保存
</Button>

Do NOT simulate disabled state
using only CSS.

Correct:

<Button disabled />

Incorrect:

<Button className="disabled-button" />

---

# 11. Loading

Use:

loading

Example:

<Button
  type="primary"
  loading
>
  保存
</Button>

For dynamic loading:

<Button
  type="primary"
  loading={loading}
>
  保存
</Button>

Use loading when:

- submitting
- saving
- creating
- deleting
- asynchronous action

The purpose is to prevent duplicate actions
and communicate asynchronous progress.

---

# 12. Icon

Use:

icon

Example:

import {
  DownloadOutlined,
} from '@ant-design/icons';

<Button
  icon={<DownloadOutlined />}
>
  下载
</Button>

Icon-only:

<Button
  shape="circle"
  icon={<DownloadOutlined />}
/>

Do not create arbitrary SVG icons
when an approved Ant Design icon exists.

---

# 13. Icon Position

If precise icon placement is required,
Ant Design documentation indicates
that the icon can be placed directly
inside Button instead of only using
the icon property.

Example:

<Button>
  <DownloadOutlined />
  下载
</Button>

Use this only when the required layout
cannot be appropriately represented
with the icon property.

---

# 14. Shape

Ant Design 4.x supports:

shape="default"

shape="circle"

shape="round"

Example:

<Button
  shape="circle"
  icon={<SearchOutlined />}
/>

Example:

<Button
  shape="round"
>
  操作
</Button>

Do not use custom border-radius CSS
when the standard Button shape API
satisfies the requirement.

---

# 15. Block

Use:

block

when the button should occupy
the full width of its parent.

Example:

<Button
  type="primary"
  block
>
  登录
</Button>

Do not manually implement
width: 100%
when Button block behavior is appropriate.

---

# 16. Link Behavior

If Button is actually intended
to navigate to another URL,
consider:

href

Example:

<Button
  type="link"
  href="/detail"
>
  查看详情
</Button>

When navigation behavior is required,
do not pretend that the element
is only a visual Button.

---

# 17. Button HTML Type

Ant Design supports:

htmlType

Examples:

htmlType="submit"

htmlType="button"

htmlType="reset"

For Form submission:

<Button
  type="primary"
  htmlType="submit"
>
  提交
</Button>

Do not confuse:

type="primary"

with:

htmlType="submit"

They represent different concepts.

---

# 18. Common Mistakes

## Mistake 1

Incorrect:

<Button type="danger">

Correct:

<Button danger>

---

## Mistake 2

Incorrect:

<button>
  新增
</button>

Correct:

<Button type="primary">
  新增
</Button>

---

## Mistake 3

Incorrect:

<Button className="primary-button">

Correct:

<Button type="primary">

---

## Mistake 4

Incorrect:

<Button
  style={{
    width: '100%',
  }}
>

when block behavior is appropriate.

Correct:

<Button block>

---

## Mistake 5

Incorrect:

<Button
  className="disabled"
>

Correct:

<Button disabled>

---

# 19. Button API Priority

When generating Button code,
follow this conceptual priority:

type
↓
shape
↓
size
↓
loading
↓
disabled

Ant Design documentation recommends this
ordering when describing Button properties.

---

# 20. Design-to-Code Mapping

When a design image contains:

Blue / emphasized primary action:

→ Button type="primary"

Neutral action:

→ Button

Dashed add action:

→ Button type="dashed"

Low-emphasis action:

→ Button type="text"

Inline navigation:

→ Button type="link"

Destructive action:

→ Button danger

Disabled:

→ Button disabled

Loading:

→ Button loading

Circular icon action:

→ Button shape="circle"

Full-width:

→ Button block

---

# 21. Button Recognition Examples

Design:

[+ 新增供应商]

Mapping:

<Button type="primary">
  新增供应商
</Button>

---

Design:

[取消] [保存]

Mapping:

<Button>
  取消
</Button>

<Button type="primary">
  保存
</Button>

---

Design:

[删除]

Mapping:

<Button danger>
  删除
</Button>

---

Design:

[查看详情]

Mapping:

<Button type="link">
  查看详情
</Button>

if the design represents
an inline low-emphasis navigation action.

---

# 22. Chinese / English Recognition

All of the following should be understood.

"按钮"

→ Button

"button"

→ Button

"增加一个按钮"

→ Button

"add a button"

→ Button

"新增"

→ Button

"primary button"

→ Button type="primary"

"主要按钮"

→ Button type="primary"

"危险按钮"

→ Button danger

"danger button"

→ Button danger

"文字按钮"

→ Button type="text"

"text button"

→ Button type="text"

"链接按钮"

→ Button type="link"

"link button"

→ Button type="link"

---

# 23. Validation

Before generating Button code:

[ ] Uses Ant Design Button

[ ] Imports Button from antd

[ ] type is a valid Ant Design 4.x value

[ ] danger is a property, not a type

[ ] size is a valid Ant Design 4.x value

[ ] shape is a valid Ant Design 4.x value

[ ] loading uses loading

[ ] disabled uses disabled

[ ] full-width uses block when appropriate

[ ] icon uses Ant Design icon when available

[ ] htmlType is used correctly inside Form

[ ] No native <button>

[ ] No custom Button implementation

[ ] No invented Ant Design API

---

# 24. Golden Rule

If Ant Design 4.x already provides
the required Button behavior or style,
use the official API.

Do not recreate it with custom CSS.

Do not invent props.

Do not replace it with native HTML.

Use:

Ant Design 4.x
+
official API
+
semantic intent
+
design recognition
