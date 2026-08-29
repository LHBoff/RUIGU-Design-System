# Card

## Basic Information

- Canonical component: Card
- Chinese name: 卡片
- Ant Design version: 4.x
- Official documentation: https://4x.ant.design/components/card-cn/
- Category: Data Display / Container

## Language Recognition

### Chinese
- 卡片
- 信息卡片
- 内容卡片
- 数据卡片
- 概览卡片

### English
- card
- content card
- info card
- data card
- dashboard card

## Decision Rules

适用于：
- Dashboard 指标
- 信息分组
- 内容模块
- 图片内容
- 数据概览
- 相关信息集合

不要为了视觉效果给每个很小的内容都创建 Card。

## Example

```tsx
<Card
  title="供应商信息"
  extra={<a>查看更多</a>}
>
  内容
</Card>
```
