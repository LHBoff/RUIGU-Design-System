# Button

## Basic Information

* Canonical component: `Button`
* Chinese name: 按钮
* Ant Design version: 4.x
* Official documentation: https://4x.ant.design/components/button-cn/
* Category: Action

---

## Language Recognition

### Chinese

```text
按钮
操作按钮
主按钮
默认按钮
虚线按钮
文本按钮
链接按钮
新增按钮
删除按钮
保存按钮
提交按钮
确认按钮
取消按钮
```

### English

```text
button
action button
primary button
default button
dashed button
text button
link button
add button
delete button
save button
submit button
confirm button
cancel button
```

### Mixed

```text
增加一个 button
加一个 Button
primary 按钮
delete button
新增 primary button
加一个 danger button
```

---

## Semantic Mapping

| User intent | Ant Design mapping              |
| ----------- | ------------------------------- |
| 主行动点        | `type="primary"`                |
| 一般行动        | default Button                  |
| 危险操作        | `danger`                        |
| 异步提交        | `loading`                       |
| 暂不可用        | `disabled`                      |
| 导航          | `type="link"` / navigation link |
| 文本级操作       | `type="text"`                   |
| 图标操作        | `icon` / `shape`                |
| 多个次级操作      | Dropdown / Dropdown.Button      |

---

## Decision Rules

### Primary

如果按钮代表当前区域最主要的行动：

```tsx
<Button type="primary">新增供应商</Button>
```

一个操作区域一般只保留一个主要 Primary Action。

---

### Destructive

以下语义应该识别为危险操作：

```text
删除
移除
永久删除
撤销
禁用
Destroy
Delete
Remove
Revoke
```

例如：

```tsx
<Button danger>删除</Button>
```

如果操作不可逆或风险较高，需要进一步考虑：

```text
Button
+
Popconfirm / Modal.confirm
```

---

### Loading

异步操作应该避免用户重复提交：

```tsx
<Button type="primary" loading>
  保存中
</Button>
```

---

### More Actions

如果一个区域有多个次级操作：

```text
编辑
复制
导出
删除
移动
...
```

不要简单堆叠大量 Button。

优先考虑：

```text
Dropdown
```

或：

```text
Dropdown.Button
```

---

## Do Not Use Button When

不要因为用户说“按钮”就机械使用 Button。

如果实际意图是：

```text
页面跳转
```

应该考虑 Link / navigation。

如果实际意图是：

```text
从多个选项中选择
```

应该考虑 Select / Radio。

如果实际意图是：

```text
展开菜单
```

应该考虑 Dropdown。

---

## Common Code

```tsx
import { Button } from 'antd';

<Button type="primary">新增</Button>

<Button>取消</Button>

<Button danger>删除</Button>

<Button loading>保存中</Button>

<Button disabled>暂不可用</Button>

<Button type="link">查看详情</Button>
```

---

## Important

Do not invent Ant Design 4.x Button props.

When exact API details are required, use the official Ant Design 4.x documentation as the source of truth.
