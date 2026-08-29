# Form Pattern

## Intent

用于创建、编辑和提交结构化业务数据。

## Language Recognition

### Chinese
- 新增页
- 编辑页
- 新建
- 创建
- 表单
- 填写信息

### English
- edit form
- create form
- form page

## Component Mapping

- Form
- Form.Item
- Input
- Select
- Radio
- Cascader
- DatePicker
- Button

## Rules

- 自由文本：Input
- 固定选项：Select
- 少量互斥选项：Radio
- 层级选择：Cascader
- 日期：DatePicker
- 提交：Button type="primary"
- 取消：Button
- 异步提交：loading

必须考虑：
- required
- validation
- error state
- disabled
- loading
- submit success
- submit failure
