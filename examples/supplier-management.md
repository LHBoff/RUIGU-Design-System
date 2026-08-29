# Example: Supplier Management

## User Request

```text
帮我做一个供应商管理页面。
```

## AI Interpretation

### Page Pattern

```text
List Pattern
```

### Business Goal

```text
高效管理大量供应商数据
```

### Components

```text
Input
Select
Button
Table
Pagination
Dropdown
Popconfirm / Modal.confirm
```

### Structure

```text
供应商管理
│
├── 搜索区域
│   ├── 供应商名称 Input
│   └── 状态 Select
│
├── 操作区域
│   └── 新增供应商 Button primary
│
├── Table
│   ├── 供应商名称
│   ├── 联系人
│   ├── 状态
│   ├── 更新时间
│   └── 操作
│
└── Pagination
```

### Row Actions

```text
查看
编辑
删除
```

删除：

```text
danger
+
confirmation
```

---

## Code Direction

```tsx
<PageHeader title="供应商管理" />

<Space>
  <Input placeholder="请输入供应商名称" />

  <Select
    placeholder="请选择状态"
    options={statusOptions}
  />

  <Button type="primary">
    新增供应商
  </Button>
</Space>

<Table
  rowKey="id"
  columns={columns}
  dataSource={dataSource}
/>
```

This is a semantic example, not a complete production page.
