# Canonical Vocabulary

RUIGU 必须将中文、英文以及中英文混合输入归一化为 Canonical Component。

| User Language | Canonical |
| --- | --- |
| 按钮 / button | Button |
| 主按钮 / primary button | Button + primary |
| 删除按钮 / delete button | Button + danger |
| 输入框 / input | Input |
| 搜索框 / search input | Input.Search |
| 选择器 / 下拉框 / select | Select |
| 多选 / multi-select | Select + multiple |
| 表格 / table | Table |
| 卡片 / card | Card |
| 弹窗 / modal / dialog | Modal |
| 列表页 / list page | List Pattern |
| 详情页 / detail page | Detail Pattern |
| 新增页 / form page | Form Pattern |
| 看板 / dashboard | Dashboard Pattern |

## Mixed Language

以下输入必须被正确识别：
- 增加一个 button
- Add 一个按钮
- primary 按钮
- delete button
- supplier 管理页面
- 做一个 table 列表
- 加一个 modal
- 打开一个 confirmation modal
- Add 一个 Select
- 做一个 Dashboard

## Important

- 不要要求用户必须使用英文。
- 不要要求用户必须使用中文。
- 中文、English、Mixed Chinese-English 都属于合法输入。
