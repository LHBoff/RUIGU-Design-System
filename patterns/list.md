# List Pattern

## Intent

用于中后台管理类列表页面。

典型目标：

* 查询数据
* 筛选数据
* 查看数据
* 新增数据
* 编辑数据
* 删除数据
* 批量处理数据

## Language Recognition

```text
列表页
管理列表
数据列表
管理页面
XXX管理
XXX列表
数据管理
查询列表
list page
management page
data list
admin list
management table
```

## Recommended Structure

```text
Page
│
├── Page Header
│
├── Search / Filter Area
│   ├── Input
│   ├── Select
│   ├── DatePicker
│   └── Search / Reset
│
├── Primary Action
│   └── Button
│
├── Table
│
└── Pagination
```

## Component Mapping

| Requirement | Component                    |
| ----------- | ---------------------------- |
| 搜索文字        | Input / Input.Search         |
| 状态筛选        | Select                       |
| 日期筛选        | DatePicker                   |
| 新增          | Button primary               |
| 数据展示        | Table                        |
| 查看          | Link / secondary action      |
| 编辑          | Button / Link                |
| 删除          | danger action + confirmation |
| 更多          | Dropdown                     |
| 分页          | Pagination                   |

## Important Rules

一个页面的主要业务动作应该明确。

例如：

```text
新增供应商
```

通常应该成为主要 Primary Action。

而：

```text
编辑
删除
查看
```

属于行级操作。

不要把所有操作都设计成 Primary Button。
