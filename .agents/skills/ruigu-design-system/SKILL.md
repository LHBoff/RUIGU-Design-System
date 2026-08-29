---
name: ruigu-design-system
description: 根据原型/设计稿/自然语言命令自动识别所需 UI 组件，始终以项目实际安装的 Ant Design 版本为实现基础：有对应组件必须使用 Ant Design，无对应组件才自定义，并按设计稿进行视觉样式定制。Analyze prototypes, designs, or natural-language commands to automatically identify UI components; always implement on top of the project's actual Ant Design version—use Ant Design when a matching component exists, build custom only when none exists, and visually customize components to match the design.
---

# RUIGU Design System

## 1. Core Mission

RUIGU is an **Ant Design First Design-to-Code Skill**.

Its primary purpose is to build interfaces **on top of Ant Design**, not to create an independent UI component system.

The fundamental rule is:

> **Ant Design is the foundation. The design is the customization reference.**

When converting a design into code:

```text
Design / Prototype / Screenshot
            ↓
     Understand page
            ↓
    Identify functionality
            ↓
   Identify UI elements
            ↓
    Find Ant Design equivalent
            ↓
 ┌──────────┴──────────┐
 YES                    NO
 ↓                      ↓
Ant Design component   Custom implementation
 ↓
Apply design-specific styling
            ↓
      Build final page
```

---

# 2. Non-Negotiable Ant Design First Rule

For every UI element:

> **If Ant Design provides an appropriate component, use Ant Design.**

Do NOT recreate an existing Ant Design component with:

* native HTML
* custom JSX
* custom CSS-only components
* another UI component library
* manually constructed equivalents

Examples:

```text
Button
→ Ant Design Button

Input
→ Ant Design Input

Search
→ Ant Design Input.Search when appropriate

Select
→ Ant Design Select

Date selection
→ Ant Design DatePicker / RangePicker

Table
→ Ant Design Table

Form
→ Ant Design Form

Modal
→ Ant Design Modal

Drawer
→ Ant Design Drawer

Tabs
→ Ant Design Tabs

Pagination
→ Ant Design Pagination

Tag
→ Ant Design Tag

Badge
→ Ant Design Badge

Tooltip
→ Ant Design Tooltip

Dropdown
→ Ant Design Dropdown

Upload
→ Ant Design Upload
```

This principle applies to the entire Ant Design component system, not only the examples above.

### Mandatory Component Mapping Table

When you see any of the following elements in a design / prototype / requirement, you **MUST** use the corresponding Ant Design component. No exceptions.

| Design element | Ant Design component |
|---|---|
| 按钮 / 提交 / 新增 / 保存 / 删除 / button | `Button` |
| 输入框 / 文本框 / 名称 / 关键词 / input / text field | `Input` |
| 搜索框 / 搜索 / 查询 / search | `Input.Search` |
| 数字输入 / 数量 / number input | `InputNumber` |
| 下拉选择 / 单选下拉 / select / dropdown | `Select` |
| 多选下拉 / multi select | `Select mode="multiple"` |
| 级联选择 / 省市区 / cascader | `Cascader` |
| 树形选择 / tree select | `TreeSelect` |
| **单选框 / 单选按钮组 / radio** | **`Radio` / `Radio.Group`** |
| **复选框 / 多选框 / checkbox** | **`Checkbox` / `Checkbox.Group`** |
| 开关 / 切换 / switch / toggle | `Switch` |
| 滑块 / 滑杆 / slider | `Slider` |
| 评分 / 星级 / rate / star | `Rate` |
| 日期选择 / 日期 / date picker | `DatePicker` |
| 日期范围 / 起止日期 / range picker | `RangePicker` |
| 时间选择 / time picker | `TimePicker` |
| 穿梭框 / 左右选择 / transfer | `Transfer` |
| 上传 / 文件上传 / upload | `Upload` |
| 表单 / 提交数据 / form | `Form` + `Form.Item` |
| 表格 / 数据表 / 列表数据 / table / data grid | `Table` |
| 标签 / 状态标签 / tag | `Tag` |
| 徽标 / 红点 / 角标 / badge | `Badge` |
| 头像 / avatar | `Avatar` |
| 卡片 / card | `Card` |
| 标签页 / 页签 / tabs | `Tabs` |
| 折叠面板 / 手风琴 / collapse / accordion | `Collapse` |
| 步骤条 / 步骤 / steps | `Steps` |
| 面包屑 / breadcrumb | `Breadcrumb` |
| 下拉菜单 / 菜单 / menu / dropdown | `Dropdown` + `Menu` |
| 分页 / 页码 / pagination | `Pagination`（表格内优先用 Table pagination） |
| 时间轴 / timeline | `Timeline` |
| 树形结构 / 组织树 / tree | `Tree` |
| 列表 / list | `List` |
| 描述列表 / 详情字段 / descriptions | `Descriptions` |
| 统计数值 / 数字卡片 / statistic | `Statistic` |
| 进度条 / 进度 / progress | `Progress` |
| 分割线 / divider | `Divider` |
| **弹窗 / 对话框 / modal / dialog** | **`Modal`** |
| 抽屉 / 侧边栏弹窗 / drawer | `Drawer` |
| 气泡确认 / 删除确认 / popconfirm | `Popconfirm` |
| 气泡卡片 / 悬浮卡片 / popover | `Popover` |
| 文字提示 / 悬浮提示 / tooltip | `Tooltip` |
| 警告提示 / alert | `Alert` |
| 全局提示 / message / toast | `message` |
| 通知提醒 / notification | `notification` |
| 加载中 / 旋转加载 / spin / loading | `Spin` |
| 骨架屏 / 占位加载 / skeleton | `Skeleton` |
| 空状态 / 暂无数据 / empty | `Empty` |
| 结果页 / 成功失败页 / result | `Result` |
| 轮播 / 走马灯 / carousel | `Carousel` |
| 日历 / calendar | `Calendar` |

> If a design element is not in this table but Ant Design has a component for it, you still MUST use the Ant Design component. This table is a minimum enforcement list, not an exhaustive list.

### High-Frequency Component Implementation Notes

**Global principle for ALL components: Use Ant Design's default props and default visual structure. Do NOT manually add dividers, borders, spacing, or other elements that Ant Design already renders by default. If a default visual element is missing, you passed the wrong props — fix the props, do not patch with custom CSS.** If the design explicitly differs from Ant Design default, then customize via official props / tokens.

These components have structural details that are easy to get wrong. Follow them exactly.

**Modal / Drawer — dialogs**

**Use Ant Design Modal's DEFAULT structure. Do NOT customize visual style.**

Ant Design Modal comes with built-in structure out of the box:
- Header with `title` + close button, with a bottom divider line (border-bottom)
- Body for content
- Footer with `Cancel` (left, default) + `OK` (right, primary), with a top divider line (border-top, full-width)

**If dividers are missing, you forgot to pass `title` or `onOk`/`onCancel`. Do NOT manually add `<Divider />` or custom borders — fix the props instead.**

**Width (fixed px only):** 400 (confirm) / 520 (default) / 640 (form) / 800 (complex). Never percentage.

**Standard template — use default props, no custom footer:**
```tsx
<Modal
  title="弹窗标题"
  open={visible}
  onCancel={() => setVisible(false)}
  onOk={handleOk}
  okText="确定"
  cancelText="取消"
  width={520}
  destroyOnClose
  maskClosable={false}
>
  {/* body content */}
</Modal>
```

**Form modal:**
```tsx
<Modal
  title="编辑"
  open={visible}
  onCancel={() => setVisible(false)}
  onOk={form.submit}
  width={640}
  destroyOnClose
  maskClosable={false}
>
  <Form form={form} layout="vertical" onFinish={handleSubmit}>
    <Form.Item name="name" label="名称" rules={[{ required: true }]}>
      <Input placeholder="请输入" />
    </Form.Item>
  </Form>
</Modal>
```

**Rules:**
- Always pass `title` — without it there is no header divider.
- Always pass `onOk` + `onCancel` — without them there is no footer (and no footer divider).
- Do NOT pass `footer={null}` for action modals (only pure-info modals may omit footer).
- Do NOT pass custom `footer` unless the design explicitly requires non-standard buttons.
- Do NOT manually add `<Divider />`, `<hr />`, or custom border CSS — Ant Design renders dividers automatically when props are correct.
- Do NOT build modal with `<div>` + z-index. Always use `<Modal>`.
- Do NOT use percentage width.
- Always `destroyOnClose` + `maskClosable={false}` for forms.

**Drawer:** same rules + `placement` ("right" default), `width` or `height`.

**Table — data grid**
- Must have `columns` (each: `title`, `dataIndex`, `key`) and `dataSource`.
- Action column: use `render: () => <Space><Button type="link">编辑</Button><Button type="link" danger>删除</Button></Space>`.
- Pagination: controlled via `pagination` prop; default position is bottom-right. Use `pagination={{ position: ['bottomRight'] }}` or `false` to hide.
- Horizontal scroll: `scroll={{ x: 'max-content' }}` when columns overflow.
- Row key: always set `rowKey="id"` (or unique field).

**Form — data entry**
- Every field MUST be wrapped in `<Form.Item name="fieldName" label="标签" rules={[{ required: true }]}>`.
- Submit button: `<Button type="primary" htmlType="submit">` inside `<Form onFinish={handleSubmit}>`.
- Layout: control label/input width with `labelCol={{ span: 6 }}` `wrapperCol={{ span: 18 }}` on Form or Form.Item.
- Use `Form.useForm()` for form instance control (`validateFields`, `setFieldsValue`, `resetFields`).

**Select / Radio.Group / Checkbox.Group — selection**
- Select: provide `options={[{ label, value }]}` or `<Option>`. Enable search with `showSearch`.
- Radio.Group: use `<Radio.Group value={val} onChange={...}><Radio value={1}>A</Radio><Radio value={2}>B</Radio></Radio.Group>` or `options` prop.
- Checkbox.Group: same pattern as Radio.Group for multiple selection.
- All three are controlled: `value` + `onChange`.

**Button**
- Variants: `type="primary"` (main action), `default` (secondary), `dashed`, `text`, `link`.
- Danger: `danger` prop for destructive actions.
- Sizes: `size="large" | "middle" | "small"`.
- Loading state: `loading` prop.
- Group buttons with `<Space>` to get consistent gaps.

---

# 3. Ant Design Is the UI Foundation

The generated page should be structurally built from Ant Design wherever possible.

Prefer:

```text
Ant Design Layout
Ant Design Grid
Ant Design Space
Ant Design Flex
Ant Design Typography
Ant Design Form
Ant Design Button
Ant Design Input
Ant Design Select
Ant Design Table
Ant Design Modal
Ant Design Drawer
Ant Design Tabs
...
```

Do not interpret the design as permission to recreate the entire UI from scratch.

The design determines **what the page should look like**.

Ant Design determines **how standard UI functionality should be implemented**.

---

# 4. Design Is Not the Component Library

The provided design is a visual and functional reference.

It determines:

* page structure
* content
* layout
* hierarchy
* dimensions
* colors
* typography
* spacing
* borders
* radius
* shadows
* icons
* states
* interaction requirements

It does NOT override the requirement to use Ant Design components.

If a design button looks different from the default Ant Design Button:

```text
Use Ant Design Button
+
customize its appearance
```

Do NOT create a new custom button simply because the visual design differs.

---

# 5. Visual Customization

Ant Design components MUST be visually adapted to the supplied design when necessary.

Example:

```text
Design:
blue button
8px radius
44px height
specific typography

Implementation:

Ant Design Button
+
design-specific color
+
design-specific radius
+
design-specific height
+
design-specific typography
```

Therefore:

> **Component identity comes from Ant Design.**
>
> **Visual appearance comes from the design.**
>
> **Visual customization MUST be applied through Ant Design's theming / Design Token mechanism, not by hardcoding raw CSS values.**

When adapting visuals, always prefer:

```text
Ant Design Design Token / theme variable
+
design-specific value
=
customized component
```

Instead of:

```text
Ant Design component
+
inline style / hardcoded CSS with raw values
```

Refer to the official Ant Design design specification:

- Design values: https://ant.design/docs/spec/values
- Colors: https://ant.design/docs/spec/colors
- Typography: https://ant.design/docs/spec/font
- Spacing / grid: https://ant.design/docs/spec/grid
- Icons: https://ant.design/components/icon

Do not allow Ant Design's default appearance to override clearly specified design requirements.

---

# 6. Ant Design Version

Never hard-code a specific Ant Design major version.

First inspect the target project.

Check:

```text
package.json
package-lock.json
yarn.lock
pnpm-lock.yaml
installed dependencies
```

Determine the actual `antd` version.

Then use the APIs supported by that version.

Examples:

```text
Project uses Ant Design 4.x
→ use 4.x APIs

Project uses Ant Design 5.x
→ use 5.x APIs

Project uses Ant Design 6.x
→ use 6.x APIs
```

Never mix APIs from different major versions.

Never silently upgrade or downgrade the project's Ant Design dependency.

If the project has no Ant Design dependency, use the appropriate current official Ant Design version for the project environment unless the user specifies otherwise.

**When there is no project context (e.g. converting a Figma design / screenshot / prototype directly to code with no codebase):**

> Default output MUST be **React + TypeScript + Ant Design**.

Do not fall back to native HTML / CSS / custom JSX components. Every standard UI element MUST be rendered as an Ant Design component with an explicit `import` from `antd`, for example:

```tsx
import { Button, Input, Select, Table, Form, Modal } from 'antd';
```

Use the latest stable Ant Design version unless the user specifies otherwise. If the user later provides a project, re-align to that project's installed version.

Official source:

https://ant.design/

Official React documentation:

https://ant.design/docs/react/introduce/

Official components:

https://ant.design/components/

---

# 7. Ant Design API Is Authoritative

Do not invent Ant Design APIs.

Before using an unfamiliar component or API:

1. Verify that the component exists.
2. Verify that the API exists in the project's version.
3. Verify prop names.
4. Verify event names.
5. Verify value types.
6. Verify composition rules.

Use official public APIs.

Do not use undocumented internal APIs when a public API exists.

Do not create local copies of Ant Design's API specification.

---

# 8. Components That Do Not Exist in Ant Design

If the design contains a genuinely unique element for which Ant Design has no appropriate component:

**implement it independently.**

Do not force an unrelated Ant Design component to represent it.

Correct:

```text
No suitable Ant Design component
→ custom implementation
```

However, the custom element should still use Ant Design components for any standard UI controls inside it.

Example:

```text
Custom analytics visualization
├── Ant Design Select
├── Ant Design DatePicker
├── Ant Design Button
└── custom visualization
```

The exception applies only to the unsupported element itself.

---

# 9. Component Recognition

When analyzing a design, identify each element by:

* semantic purpose
* interaction
* content
* surrounding context
* visual structure
* state

Do not identify components only by appearance.

For example:

A rectangular field with a dropdown indicator and selectable values is likely:

```text
Ant Design Select
```

A text field with a search action may be:

```text
Ant Design Input.Search
```

A data grid with rows, columns, sorting, filtering, and pagination is likely:

```text
Ant Design Table
```

Use context to determine the correct Ant Design component.

---

# 10. Composite Components

A design region may contain multiple Ant Design components.

For example:

```text
Filter Area

Form
├── Form.Item
│   └── Input
├── Form.Item
│   └── Select
├── Form.Item
│   └── DatePicker
└── Button
```

Do not create one large custom component when the design can be naturally composed from Ant Design components.

Use Ant Design composition wherever appropriate.

---

# 11. Page Structure

Analyze the design before implementation.

Identify:

* page shell
* header
* navigation
* sidebar
* main content
* page header
* toolbars
* filters
* forms
* content cards
* tables
* lists
* dialogs
* drawers
* overlays
* pagination
* empty states
* loading states

Then construct the page primarily from Ant Design components.

---

# 12. Layout

Use Ant Design layout primitives when applicable.

Prefer the project's supported version of:

* Layout
* Row
* Col
* Space
* Grid
* Flex
* Divider

Do not replace standard Ant Design layout capabilities with unnecessary custom layout components.

Use CSS when necessary to achieve the design.

---

# 13. Interaction

If the design implies interaction, implement it.

Examples:

```text
Button
→ onClick

Input
→ value / onChange

Select
→ value / onChange

Form
→ validation / submit

Table
→ sorting / filtering / pagination when required

Modal
→ open / close

Drawer
→ open / close

Tabs
→ active state

Dropdown
→ menu interaction

Upload
→ upload behavior
```

Use the project's Ant Design version and its official APIs.

Do not create fake static UI where the design clearly represents an interactive component.

---

# 14. States

Recognize and implement states shown by the design.

Examples:

```text
default
hover
active
focus
selected
disabled
loading
error
warning
success
checked
unchecked
open
closed
expanded
collapsed
```

Use Ant Design's native state mechanisms whenever available.

Customize their visual appearance to match the design.

---

# 15. Colors

For Ant Design components:

**the design's colors take precedence over Ant Design's default visual colors.**

Identify:

* primary color
* secondary color
* background
* surface
* border
* divider
* text
* secondary text
* disabled text
* success
* warning
* error
* info

**Map every color to an Ant Design color token. Do not hardcode hex/rgb values directly.**

| Design role | Ant Design 4.x (less variable) | Ant Design 5.x (Design Token) |
|---|---|---|
| 主色 / primary | `@primary-color` | `colorPrimary` |
| 成功 / success | `@success-color` | `colorSuccess` |
| 警告 / warning | `@warning-color` | `colorWarning` |
| 错误 / error | `@error-color` | `colorError` |
| 信息 / info | `@info-color` | `colorInfo` |
| 主文字 | `@text-color` | `colorText` |
| 次文字 | `@text-color-secondary` | `colorTextSecondary` |
| 禁用文字 | `@disabled-color` | `colorTextDisabled` |
| 边框 | `@border-color-base` | `colorBorder` |
| 分割线 | `@border-color-split` | `colorBorderSecondary` |
| 背景 | `@background-color-base` | `colorBgLayout` |
| 组件背景 | `@component-background` | `colorBgContainer` |

Apply them through the project's version-supported theming mechanism:

- **Ant Design 4.x**: less variables (`@primary-color`), `ConfigProvider`, or `theme` option
- **Ant Design 5.x**: `ConfigProvider` with `theme.token` / `theme.components`

Do not globally modify the entire Ant Design theme merely to reproduce one component.

Prefer the smallest appropriate scope (component-level token > global token > raw CSS).

---

# 16. Typography

Preserve the design's:

* font family
* font size
* font weight
* line height
* letter spacing
* hierarchy

**Use Ant Design Typography components for text content.** Prefer:

- `Typography.Title` (levels 1-5) for headings
- `Typography.Text` for body text, with `type` (secondary / success / warning / danger) and `strong` / `disabled` / `mark` / `code` props
- `Typography.Paragraph` for paragraphs, with `ellipsis` / `copyable`

**Map font sizes to Ant Design's type scale.** Ant Design default font size阶梯:

| Level | Size | Usage |
|---|---|---|
| 标题1 | 38px | page hero title |
| 标题2 | 30px | section title |
| 标题3 | 24px | card title |
| 标题4 | 20px | subsection title |
| 标题5 | 16px | small heading |
| 正文 | 14px | body text (default) |
| 辅助文字 | 12px | helper / caption |

If the design uses a different size, preserve it but apply it through Ant Design's typography token (`@font-size-base` in 4.x / `fontSize` in 5.x) or the Typography component's `style`, not by replacing the component with raw `<div>`.

Do not allow default typography to overwrite clearly specified design requirements.

---

# 17. Spacing and Dimensions

Preserve meaningful values from the design:

* width
* height
* padding
* margin
* gap
* alignment
* row height
* column width
* container dimensions

**Align spacing to Ant Design's 8px grid system.** Ant Design uses an 8px base unit; preferred spacing values are multiples of 8:

```text
4, 8, 12, 16, 20, 24, 32, 40, 48, 56, 64 ...
```

**Use Ant Design layout primitives for spacing instead of raw CSS margin/padding whenever possible:**

- `Space` — for gaps between components (size: `small`=8, `middle`=16, `large`=24, or custom number)
- `Row` / `Col` with `gutter` — for grid layouts
- `Flex` — for flexbox layouts with `gap`
- `Divider` — for section separators

If the design specifies a spacing value that is not a multiple of 8, preserve the design value but note the deviation. Do not arbitrarily round it to 8 if it would break the design.

Use responsive and reusable layout values where appropriate.

Do not arbitrarily normalize the design to default Ant Design spacing.

---

# 18. Icons

When an appropriate Ant Design icon exists:

**use the Ant Design icon.**

If no suitable icon exists:

* use an existing project icon;
* use the provided design asset;
* or implement an appropriate custom icon.

Do not substitute emoji for interface icons.

---

# 19. Existing Project

When working inside an existing project:

1. inspect the project;
2. detect the installed Ant Design version;
3. preserve the existing architecture;
4. reuse existing components where appropriate;
5. reuse existing routing;
6. reuse existing state management;
7. reuse existing styling conventions;
8. avoid unnecessary dependencies;
9. do not migrate frameworks without instruction.

The existing project architecture takes precedence over unnecessary restructuring.

---

# 20. Other UI Libraries

If the project already uses another UI library:

Do not automatically rewrite the entire project.

If the user explicitly requests Ant Design:

implement the requested page using Ant Design while minimizing unnecessary architectural changes.

Do not mix multiple UI libraries for the same standard component without a clear reason.

---

# 21. Responsive Design

If multiple design breakpoints are provided:

implement the corresponding responsive behavior.

If only one viewport is provided:

preserve the supplied design exactly at that viewport and infer reasonable responsive behavior for other sizes without redesigning the page.

---

# 22. Accessibility

Preserve:

* semantic labels
* keyboard interaction
* focus behavior
* accessible names
* form labels
* appropriate disabled states
* meaningful controls

Use Ant Design's built-in accessible behavior whenever available.

---

# 23. Code Quality

Generated code must be:

* valid
* maintainable
* componentized
* typed where the project uses TypeScript
* compatible with the existing project
* free of invented Ant Design APIs
* free of unnecessary dependencies

**Every standard UI element MUST be imported from `antd`.** Before delivering, confirm that the code contains `import { ... } from 'antd'` and that each button / input / select / table / modal / form etc. is an Ant Design component, not a native `<button>` / `<input>` / custom div.

Do not leave critical functionality as pseudocode.

Do not leave obvious placeholder UI where implementation is expected.

---

# 24. Validation — Ant Design First

Before completing the task, verify:

### Component validation

For every standard UI element:

```text
Does Ant Design provide an appropriate component?

YES
→ Is the generated implementation actually using it?

NO
→ replace the custom implementation with Ant Design.
```

### Custom component validation

For every custom element:

```text
Does an appropriate Ant Design equivalent actually exist?

YES
→ replace it with Ant Design.

NO
→ custom implementation is allowed.
```

### Version validation

Verify:

```text
All Ant Design imports are valid.
All APIs match the installed version.
No major-version APIs are mixed.
```

### Visual validation

Verify the generated page against the design:

```text
color
typography
spacing
dimensions
radius
border
shadow
alignment
icons
states
```

### Interaction validation

Verify:

```text
buttons
inputs
selects
forms
tables
pagination
dialogs
drawers
tabs
dropdowns
uploads
```

according to what the design requires.

---

# 25. Priority Rules

When rules conflict, use this priority:

```text
1. Existing project architecture
2. Ant Design component system
3. Ant Design version/API compatibility
4. Design functionality
5. Design visual requirements
6. Custom implementation only when necessary
```

The important constraint is:

> **Visual differences must not be used as a reason to replace an available Ant Design component with a custom component.**

Instead:

```text
Ant Design component
+
custom styling
=
final implementation
```

---

# 26. User Interaction

The user should be able to provide:

* a Figma design
* a screenshot
* a prototype
* a wireframe
* a design specification
* natural-language requirements

The user should NOT need to manually specify:

```text
which component to use
which Ant Design component corresponds to it
which API to use
which standard interaction to implement
```

RUIGU should determine these automatically.

A simple request such as:

> Build this page from the design.

should be sufficient.

---

# 27. Final Execution Algorithm

For every Design-to-Code task:

```text
INPUT
Design / Prototype / Screenshot / Figma / Requirement

↓

1. Inspect project
2. Detect installed Ant Design version
   ├─ If project exists → use its installed antd version
   └─ If no project (pure Figma / screenshot / prototype) → default to React + TypeScript + latest stable Ant Design, MUST import from 'antd'
3. Understand page structure
4. Identify page functionality
5. Identify UI elements
6. Cross-check EVERY identified element against the Mandatory Component Mapping Table (Section 2) — if it's in the table, the mapped Ant Design component is NON-NEGOTIABLE
7. Determine semantic purpose
8. Check whether Ant Design provides an appropriate component
9. If YES → MUST use Ant Design
10. If NO → custom implementation allowed
11. Verify official API for the project version
12. Build page using Ant Design as the foundation
13. Apply design-specific visual styling via Ant Design Design Token / theming mechanism
14. Implement required interaction
15. Validate component usage
16. Validate API/version
17. Validate visual fidelity (colors → tokens, typography → type scale, spacing → 8px grid)
18. Validate interaction
19. Validate code
20. Deliver final implementation
```

---

# 28. Ultimate Rule

**Ant Design First.**

If Ant Design has the component:

> **Use Ant Design.**

If Ant Design does not have the component:

> **Build it yourself.**

If the Ant Design component does not visually match the design:

> **Customize the Ant Design component. Do not replace it unnecessarily.**

The goal is not to make a page that merely looks like Ant Design.

The goal is to build the page **with Ant Design as its foundational UI component system**, while using the supplied design as the source of content, layout, visual customization, and interaction requirements.

---

# 29. Reference Files

This skill bundles detailed reference documents. Read them when you need deeper guidance:

### Core decision files — read first when selecting page structure or components

- `core/component-mapping.md` — how to recognize user intent and map UI elements to the correct Ant Design component (do not map words blindly).
- `core/page-patterns.md` — page-level patterns (List / Detail / Form / Dashboard etc.) to identify before composing components.
- `core/ant-design-rules.md` — Ant Design usage rules and conventions to follow.

### Component references — read when implementing a specific component

- `components/button.md` — Button variants, props, and usage.
- `components/input.md` — Input / Input.Search usage.
- `components/select.md` — Select usage.
- `components/table.md` — Table columns, sorting, filtering, pagination.
- `api/button-api.md` — Button API reference.
