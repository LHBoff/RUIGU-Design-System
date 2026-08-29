# Detail Pattern

## Intent

展示一个业务实体的完整信息。

## Language Recognition

### Chinese
- 详情页
- 查看详情
- 信息详情
- 供应商详情
- 用户详情
- 订单详情

### English
- detail page
- detail view
- details

## Recommended Structure

```
Page
├── Breadcrumb / Context
├── Header
│   ├── Title
│   ├── Status
│   └── Actions
├── Summary
├── Information Sections
├── Related Data
└── Footer Actions
```

## Component Mapping

通常考虑：
- Card
- Descriptions
- Tag
- Table
- Button

Card 用于信息分组。
不要把每一个字段都单独做成 Card。
