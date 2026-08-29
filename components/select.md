# Select

## Basic Information

- Canonical component: Select
- Chinese name: 选择器 / 下拉选择器
- Ant Design version: 4.x
- Official documentation: https://4x.ant.design/components/select-cn/
- Category: Data Entry

## Language Recognition

### Chinese
- 选择器
- 下拉选择
- 下拉框
- 选择框
- 单选下拉
- 多选下拉
- 供应商选择
- 选择用户

### English
- select
- dropdown select
- selector
- single select
- multi-select

### Mixed
- 加一个 select
- 增加一个选择器
- supplier select
- 多选 select
- select 用户

## Semantic Mapping

- 单选 -> Select
- 多选 -> `mode="multiple"`
- 标签选择 -> `mode="tags"`
- 大量选项 -> consider search
- 层级选择 -> Cascader
- 少量互斥选项 -> consider Radio

## Examples

```tsx
<Select
  placeholder="请选择供应商"
  options={[
    {
      value: '1',
      label: '供应商 A',
    },
    {
      value: '2',
      label: '供应商 B',
    },
  ]}
/>
```

Multiple:

```tsx
<Select
  mode="multiple"
  placeholder="请选择供应商"
/>
```

## Important

- Do not use Select merely because a dropdown visual style looks convenient.
- The user intent must actually be selection from predefined options.
- Exact API follows Ant Design 4.x documentation.
