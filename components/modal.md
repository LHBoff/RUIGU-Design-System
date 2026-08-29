# Modal

## Basic Information

- Canonical component: Modal
- Chinese name: 弹窗 / 对话框 / 模态框
- Ant Design version: 4.x
- Official documentation: https://4x.ant.design/components/modal-cn/
- Category: Feedback / Overlay

## Language Recognition

### Chinese
- 弹窗
- 对话框
- 模态框
- 确认弹窗
- 编辑弹窗
- 删除确认弹窗

### English
- modal
- dialog
- confirmation dialog
- confirm modal

## Decision Rules

适用于：
- 当前页面内完成一个独立任务
- 确认重要操作
- 编辑少量信息
- 需要用户明确确认的操作

如果只是简单确认：
- Modal.confirm

或者：
- Popconfirm

如果需要填写复杂信息：
- Modal

或者根据内容复杂度考虑 Drawer / 独立页面。

## Example

```tsx
<Modal
  title="删除供应商"
  open={open}
  confirmLoading={loading}
  onOk={handleOk}
  onCancel={handleCancel}
>
  确定要删除该供应商吗？
</Modal>
```

危险确认应该使用明确的 destructive semantics。
