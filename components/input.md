# Input

## Basic Information

- Canonical component: Input
- Chinese name: 输入框
- Ant Design version: 4.x
- Official documentation: https://4x.ant.design/components/input-cn/
- Category: Data Entry

## Language Recognition

### Chinese
- 输入框
- 文本框
- 搜索框
- 搜索输入框
- 密码框
- 文本域
- 多行输入

### English
- input
- text input
- text field
- search input
- search box
- password input
- textarea
- text area

### Mixed
- 加一个 input
- 增加一个输入框
- search input
- 加一个搜索 input
- password 输入框

## Semantic Mapping

- 普通文本 -> Input
- 搜索 -> Input.Search
- 密码 -> Input.Password
- 多行文本 -> Input.TextArea

## Decision Rules

如果用户需要自由输入文字：
- Input

如果用户需要从固定选项中选择：
- 不要使用 Input

应该考虑：
- Select
- Radio
- Cascader

## Examples

```tsx
<Input placeholder="请输入供应商名称" />

<Input.Search placeholder="搜索供应商" />

<Input.Password placeholder="请输入密码" />

<Input.TextArea
  rows={4}
  placeholder="请输入备注"
/>
```

在表单中：

```tsx
<Form.Item
  name="supplierName"
  label="供应商名称"
>
  <Input placeholder="请输入供应商名称" />
</Form.Item>
```

Exact API should follow the official Ant Design 4.x documentation.
