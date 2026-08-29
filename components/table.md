# Table

## Basic Information

- Canonical component: Table
- Chinese name: 表格
- Ant Design version: 4.x
- Official documentation: https://4x.ant.design/components/table-cn/
- Category: Data Display

## Language Recognition

- 表格
- 数据表格
- 数据列表
- 管理列表
- table
- data table
- grid
- data grid
- supplier table

## Decision Rules

使用 Table 的典型场景：
- 多条结构化数据
- 行列关系明显
- 需要排序
- 需要筛选
- 需要分页
- 需要选择
- 需要行级操作

### Standard Management List

```
Page
├── Page Header
├── Search / Filter
├── Primary Action
├── Table
└── Pagination
```

### Row Actions

常见：
- 查看
- 编辑
- 删除
- 更多

删除属于危险操作，应考虑：
- danger
- \+
- confirmation

## States

必须考虑：
- Loading
- Empty
- Error
- Pagination
- Selection
- Sorting
- Filtering

## Example

```tsx
<Table
  rowKey="id"
  columns={columns}
  dataSource={dataSource}
  pagination={{
    pageSize: 20,
  }}
/>
```

Exact API follows Ant Design 4.x documentation.
