# RUIGU Table

## Component

Table

## Ant Design Version

按项目实际安装版本（检测见 SKILL.md 第 7 节）；无项目时默认最新稳定版

## Official Documentation

https://ant.design/components/table/

---

# 1. Component Identification

Use Table when the user needs to display structured
records in rows and columns.

Chinese keywords:

- 表格
- 数据表
- 数据表格
- 列表
- 数据列表
- 管理列表
- 管理表格
- 信息表格
- 记录列表
- 数据记录
- 结果列表
- 查询结果
- 用户列表
- 供应商列表
- 商品列表
- 订单列表

English keywords:

- table
- data table
- data grid
- data list
- records
- management table
- result table
- user table
- supplier table
- order table
- product table

Chinese-English mixed examples:

- 增加一个 table
- 加一个数据表格
- 做一个 supplier table
- 增加一个用户列表
- 加一个 data table
- 创建一个管理列表

All should be interpreted as Table-related requirements
when the content is structured into rows and columns.

---

# 2. Ant Design Mapping

RUIGU Table MUST map to:

antd.Table

Import:

import { Table } from 'antd';

Do not replace Ant Design Table with:

<table>

Do not create a custom Table component when Ant Design
can satisfy the requirement.

---

# 3. Table Recognition

When analyzing a design image,
identify a Table when the content has:

- multiple rows
- consistent columns
- column headers
- structured records
- repeated data
- row-level actions

Typical visual structure:

┌──────────┬──────────┬──────────┬──────────┐
│ 供应商    │ 联系人    │ 状态      │ 操作      │
├──────────┼──────────┼──────────┼──────────┤
│ ABC公司  │ 张三      │ 启用      │ 编辑      │
├──────────┼──────────┼──────────┼──────────┤
│ DEF公司  │ 李四      │ 停用      │ 编辑      │
└──────────┴──────────┴──────────┴──────────┘

This should normally map to:

Table

---

# 4. Table vs List

This distinction is important.

Use Table when:

- information is organized into columns
- records share the same column structure
- headers are present
- users need to compare multiple attributes

Example:

供应商 | 联系人 | 状态 | 操作

→ Table

Use a simpler List pattern when:

- records do not require multiple columns
- each item is primarily a single content block
- the interface behaves more like a feed or simple list

Do not automatically map every vertical list
to Table.

---

# 5. Column Recognition

When analyzing a table design,
identify:

- column title
- column content
- column type
- alignment
- width
- sorting
- filtering
- row actions

Example:

供应商名称
→ text column

联系人
→ text column

状态
→ status column

操作
→ action column

---

# 6. Column Definition

When generating React + TypeScript,
use Ant Design Table columns.

Example:

const columns = [
  {
    title: '供应商名称',
    dataIndex: 'name',
    key: 'name',
  },
  {
    title: '联系人',
    dataIndex: 'contact',
    key: 'contact',
  },
  {
    title: '状态',
    dataIndex: 'status',
    key: 'status',
  },
];

Then:

<Table
  columns={columns}
  dataSource={data}
/>

---

# 7. Row Actions

If a table contains actions such as:

- 编辑
- 删除
- 查看
- 详情
- 启用
- 停用
- Edit
- Delete
- View
- Details

Use Ant Design components for the action.

Example:

render: (_, record) => (
  <Space>
    <Button type="link">
      编辑
    </Button>

    <Button
      type="link"
      danger
    >
      删除
    </Button>
  </Space>
)

Do not create custom clickable HTML elements.

---

# 8. Status Column

When a table contains status information:

Examples:

启用
停用
处理中
已完成
失败

Consider appropriate Ant Design components
such as:

Tag

Badge

Typography

depending on the visual and semantic requirement.

Do not use arbitrary custom status components
when an Ant Design component can satisfy the design.

---

# 9. Sorting

If the design indicates sortable columns:

Examples:

- ↑
- ↓
- sort
- 排序
- 升序
- 降序

Use Ant Design Table column sorting APIs.

Example:

{
  title: '创建时间',
  dataIndex: 'createdAt',
  sorter: true,
}

Do not build a custom sorting interaction
when Ant Design Table supports it.

---

# 10. Filtering

If the design provides filtering directly
inside table columns:

Consider Ant Design Table filtering APIs.

Example:

{
  title: '状态',
  dataIndex: 'status',
  filters: [
    {
      text: '启用',
      value: 'enabled',
    },
    {
      text: '停用',
      value: 'disabled',
    },
  ],
}

Do not create a custom filter mechanism
when Ant Design Table can satisfy the requirement.

---

# 11. Selection

If the table contains:

- checkboxes
- batch selection
- 全选
- 批量删除
- 批量操作

Use Ant Design Table rowSelection.

Example:

const rowSelection = {
  onChange: (selectedRowKeys, selectedRows) => {
    // handle selection
  },
};

<Table
  rowSelection={rowSelection}
  columns={columns}
  dataSource={data}
/>

Do not create custom checkbox selection
when Ant Design Table supports the requirement.

---

# 12. Pagination

If the table design contains pagination:

Example:

上一页 1 2 3 4 5 下一页

Use Ant Design Table pagination
or Ant Design Pagination depending on the page architecture.

For a standard data table:

<Table
  pagination={{
    pageSize: 20,
  }}
/>

If pagination needs to be independently positioned:

Use:

<Pagination />

Do not build custom pagination controls.

---

# 13. Empty State

If there is no data:

Examples:

暂无数据
No Data
No Results

Use Ant Design Table empty behavior
or Empty component when appropriate.

Do not create custom empty-state implementations
unless required by the design.

---

# 14. Loading State

When table data is loading:

Use:

<Table loading />

Example:

<Table
  loading={loading}
  columns={columns}
  dataSource={data}
/>

Do not create a custom loading overlay
when Ant Design Table loading can satisfy the requirement.

---

# 15. Expandable Rows

If the design shows:

> row
> ↓
> additional detail content

Consider Ant Design Table expandable rows.

Example:

<Table
  expandable={{
    expandedRowRender: (record) => (
      <div>
        {record.description}
      </div>
    ),
  }}
/>

Do not create a custom accordion inside every row
if Ant Design Table expandable behavior is appropriate.

---

# 16. Fixed Columns

If the design requires:

- 固定左侧列
- 固定右侧操作列
- fixed column
- sticky action column

Use Ant Design Table column:

fixed

Example:

{
  title: '操作',
  key: 'action',
  fixed: 'right',
}

Do not implement custom CSS positioning
when the Ant Design Table API can satisfy the requirement.

---

# 17. Scroll

If the table is wider than the available content area:

Consider Ant Design Table scroll.

Example:

<Table
  scroll={{
    x: 1200,
  }}
/>

Do not manually recreate table scrolling
unless necessary.

---

# 18. Visual Analysis Rules

When analyzing a design image,
do not identify Table only by visible borders.

A Table can exist without strong borders.

Look for:

1. Column headers
2. Repeated rows
3. Aligned values
4. Repeated record structure
5. Row actions
6. Selection controls
7. Pagination
8. Sorting
9. Filtering

If these characteristics exist,
strongly consider Table.

**Visual Mode（模式前提，见 SKILL.md 第 2 节）：** 以上视觉结构（表头、重复行、对齐列等）仅用于**识别 Table 组件类型**，不用于照抄图片中的边框样式 / 行列配色 / 单元格圆角等视觉。默认组件规范优先模式下，Table 呈现 Ant Design 默认样式。

---

# 19. Table vs Card

Do not confuse Table with Card.

Use Card when:

- each item is an independent content block
- content is grouped inside a visual container
- cards may have different internal structures

Use Table when:

- records share consistent fields
- users compare values across columns

Example:

供应商名称 | 联系人 | 电话 | 状态

→ Table

Supplier Card
Name
Contact
Description
Actions

→ Card

---

# 20. Management Page Recognition

When the user requests:

- 用户管理
- 供应商管理
- 商品管理
- 订单管理
- 客户管理
- 账号管理

and the design contains structured records:

Use:

Table

as the primary data display component.

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

---

# 21. Code Generation

When generating React + TypeScript:

Use:

import {
  Table,
  Button,
  Space,
} from 'antd';

Example:

const columns = [
  {
    title: '供应商名称',
    dataIndex: 'name',
    key: 'name',
  },
  {
    title: '联系人',
    dataIndex: 'contact',
    key: 'contact',
  },
  {
    title: '状态',
    dataIndex: 'status',
    key: 'status',
  },
  {
    title: '操作',
    key: 'action',
    render: (_, record) => (
      <Space>
        <Button type="link">
          编辑
        </Button>

        <Button
          type="link"
          danger
        >
          删除
        </Button>
      </Space>
    ),
  },
];

<Table
  rowKey="id"
  columns={columns}
  dataSource={data}
/>

---

# 22. Data Source

Table should normally use:

dataSource

Example:

<Table
  dataSource={data}
/>

Each record should have a stable key.

Prefer:

rowKey="id"

when the data contains an id.

Do not generate unstable random keys
for normal business records.

---

# 23. Chinese / English Recognition

The following should map correctly.

"增加一个表格"

→ Table

"增加一个 table"

→ Table

"做一个数据表"

→ Table

"增加一个 data table"

→ Table

"做一个供应商列表"

→ Table
when the design represents structured columns.

"做一个用户管理列表"

→ Table
when the page contains structured records.

"Add a table"

→ Table

"Add a data table"

→ Table

---

# 24. Custom Component Rule

Only create a custom data grid
when Ant Design Table cannot satisfy the requirement.

Before creating a custom table:

1. Check Table API.
2. Check sorting.
3. Check filtering.
4. Check selection.
5. Check pagination.
6. Check expandable rows.
7. Check fixed columns.
8. Check scrolling.
9. Check loading.
10. Check empty state.

Only create a custom component
if the actual requirement cannot be achieved
with Ant Design Table or composition with other
Ant Design components.

---

# 25. Validation

Before generating final code verify:

[ ] Table is semantically appropriate

[ ] Ant Design Table is used

[ ] Correct columns are identified

[ ] dataIndex is appropriate

[ ] rowKey is stable

[ ] Row actions use Ant Design components

[ ] Selection uses rowSelection when appropriate

[ ] Sorting uses Table sorting APIs when appropriate

[ ] Filtering uses Table filtering APIs when appropriate

[ ] Pagination uses Ant Design pagination

[ ] Loading uses Table loading

[ ] Empty state uses Ant Design Empty or Table behavior

[ ] No custom Table implementation

[ ] No native table replacement

[ ] No other UI library

---

# 26. Official Source

Use Ant Design documentation as the authoritative
reference for Table API and behavior.

Official documentation:

https://ant.design/components/table/
