# RUIGU Button

## Component

Button

## Ant Design Version

Ant Design 4.x

## Official Documentation

https://4x.ant.design/components/button-cn/

---

# 1. Component Identification

Use Button when the user needs an interactive action.

Chinese keywords:

- 按钮
- 按键
- 操作按钮
- 新增按钮
- 添加按钮
- 创建按钮
- 保存按钮
- 提交按钮
- 确定按钮
- 取消按钮
- 删除按钮
- 编辑按钮
- 查询按钮
- 搜索按钮
- 主要按钮
- 次要按钮

English keywords:

- button
- action button
- primary button
- secondary button
- create button
- add button
- save button
- submit button
- confirm button
- cancel button
- delete button
- edit button
- search button

Chinese-English mixed examples:

- 增加一个 button
- 添加 primary button
- 加一个 delete button
- 做一个新增 Button
- 增加一个主要 action button

All should be interpreted as Button-related requirements.

---

# 2. Ant Design Mapping

RUIGU Button MUST map to:

antd.Button

Import:

import { Button } from 'antd';

Do not replace it with:

<button>

Do not create a custom Button component when Ant Design Button
can satisfy the requirement.

---

# 3. Button Type

Map user intent to Ant Design Button type.

## Primary

Use when the action is the main action of the current area.

Examples:

- 新增
- 创建
- 提交
- 保存
- 确定
- 创建供应商
- 新建订单

Mapping:

<Button type="primary">
  新增
</Button>

---

## Default

Use for secondary or neutral actions.

Examples:

- 取消
- 返回
- 普通操作
- 次要操作

Mapping:

<Button>
  取消
</Button>

---

## Dashed

Use when the UI specifically requires a dashed button
or an add/create affordance represented by a dashed style.

Mapping:

<Button type="dashed">
  添加
</Button>

Do not choose dashed merely because the user says "添加".
Consider the visual design and interaction context.

---

## Text

Use for low-emphasis actions.

Mapping:

<Button type="text">
  编辑
</Button>

---

## Link

Use when the action visually behaves like a link.

Mapping:

<Button type="link">
  查看详情
</Button>

---

# 4. Danger

Use danger for destructive actions.

Examples:

- 删除
- 移除
- 永久删除
- 清空
- 停用
- 作废

Mapping:

<Button danger>
  删除
</Button>

If the action is destructive and confirmation is appropriate,
consider pairing the action with Modal or Popconfirm.

---

# 5. Loading

Use loading when the action is being processed.

Examples:

- 提交中
- 保存中
- 创建中
- 上传中

Mapping:

<Button loading>
  保存
</Button>

Do not simulate loading with custom CSS.

---

# 6. Disabled

Use disabled when the action cannot currently be performed.

Examples:

- 当前条件下不可操作
- 权限不足
- 表单未完成
- 数据状态不允许操作

Mapping:

<Button disabled>
  提交
</Button>

Do not use CSS alone to simulate a disabled state.

---

# 7. Visual Design Mapping

When analyzing a design image:

A rectangular clickable element containing an action label
should normally be considered a Button candidate.

Examples:

蓝色实心按钮
→ Button
→ type="primary"

灰色默认按钮
→ Button
→ default

红色删除按钮
→ Button
→ danger

文字形式操作
→ Button
→ type="text"

链接形式操作
→ Button
→ type="link"

However, visual appearance alone is not sufficient.

Also consider:

- semantic intent
- surrounding elements
- interaction
- hierarchy
- page context

---

# 8. Button Group

When multiple actions are visually grouped,
consider using:

Space

or an appropriate Ant Design grouping pattern.

Example:

<Space>
  <Button>取消</Button>
  <Button type="primary">确定</Button>
</Space>

Do not create a custom button group if Ant Design components
can satisfy the requirement.

---

# 9. Icon Button

If the design contains an icon-only action,
use Ant Design Button together with an appropriate icon.

Do not create a custom clickable div.

Example:

<Button
  type="text"
  icon={<SearchOutlined />}
/>

---

# 10. Semantic Priority

When deciding Button type, use this priority:

1. User intent
2. Business importance
3. Destructive state
4. Visual hierarchy
5. Design reference

Do not select a Button type only from color.

For example:

"删除"

even if the design is visually neutral,

should be evaluated as a destructive action.

---

# 11. Code Generation Rule

When generating React + TypeScript:

Prefer:

import { Button } from 'antd';

Then:

<Button type="primary">
  新增
</Button>

Never generate:

<button className="primary-button">
  新增
</button>

when Ant Design Button is appropriate.

---

# 12. Validation

Before generating final code verify:

[ ] Component is Button

[ ] Import comes from antd

[ ] Correct Ant Design 4.x API is used

[ ] Button type matches intent

[ ] danger is used for destructive actions when appropriate

[ ] loading is used for loading state

[ ] disabled is used for disabled state

[ ] No custom Button implementation

[ ] No native button replacement

---

# 13. Official Source

Use Ant Design 4.x documentation as the authoritative
reference for Button API and behavior.

Official documentation:

https://4x.ant.design/components/button-cn/
