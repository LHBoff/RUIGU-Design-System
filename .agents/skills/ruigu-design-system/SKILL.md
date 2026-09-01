---
name: ruigu-design-system
description: 锐锢中台组件库，基于项目实际安装版本的 Ant Design 构建。根据原型、设计稿或自然语言需求自动匹配并使用锐锢中台组件，优先复用已有组件，无对应组件时才进行扩展或自定义，并遵循锐锢设计规范完成视觉样式定制。默认按组件库规范（Ant Design 默认样式）生成页面，图片视觉不参与实现；仅当识别到「设计稿/设计图」等指向性文案时，才参考图片视觉进行定制。Analyze prototypes, designs, or natural-language commands to automatically identify UI components; always implement on top of the project's actual Ant Design version—use Ant Design when a matching component exists, build custom only when none exists. By default, build with the Ant Design component library's standard style; only reference the visual style of an uploaded image when explicit visual-reference wording (e.g. "design draft / design image") is detected.
---
# RUIGU Design System
## 1. Core Mission
RUIGU is an **Ant Design First Design-to-Code Skill**.
Its primary purpose is to build interfaces **on top of Ant Design**, not to create an independent UI component system.
The fundamental rule is:
> **Ant Design is the foundation. Default Ant Design style is the baseline. Only customize when the design explicitly differs from default.**

**DEFAULT FIRST:** Use Ant Design components with their default props and default blue theme. Do NOT proactively change colors, layout, spacing, or typography. Only deviate from default when the design clearly requires it.

**VISUAL MODE FIRST (最高优先级):** 在分析任何输入之前，必须先完成「视觉模式判定」（见第 2 节）。**默认组件规范优先**——上传图片仅作结构/内容/功能参考，视觉一律采用 Ant Design 默认规范；**仅当识别到「设计稿/设计图」等指向性文案时**，才参考图片视觉进行定制。本节及全文所有"设计明确要求 / design clearly requires"均以第 2 节的模式判定为准。

When converting a design into code:
```text
Design / Prototype / Screenshot / Natural-language command
            ↓
   STEP 0: Visual Mode Detection（第 2 节）
     ├─ 含视觉参考触发词（设计稿/设计图/高保真…）→ Visual-Reference Mode
     └─ 默认（无触发词 / 有强制组件规范词）→ Component-First Mode
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
Apply structure & visual per mode:
 ├─ Component-First Mode → 结构按第 12 节规范组织 + Ant Design 默认样式，忽略图片布局与视觉
 └─ Visual-Reference Mode → 采用图片布局 + 按图片视觉经官方 Token 定制（仅不同处）
            ↓
      Build final page
```
---
# 2. Visual Mode — Component-First by Default（视觉模式判定）

## 2.1 核心原则
> **模式判定先行：在分析任何输入之前，必须先判定模式。默认组件规范优先——结构与视觉均按 Ant Design 规范，图片参考仅在明确触发时启用。**

Ant Design 组件体系是本 Skill 的唯一实现基础（第 3 节）。输入图片存在两种"参考维度"，由模式分别决定是否采用：

| 参考维度 | 含义 | 组件规范优先（默认） | 视觉参考（仅触发） |
|---|---|---|---|
| **内容维度** | 有哪些字段、操作、数据、状态、文案 | ✅ 提取 | ✅ 提取 |
| **结构维度** | 如何排布：上下/左右、分组、每行几个、区域分配 | ❌ 不采用，按第 12 节规范重新组织 | ✅ 采用图片布局 |
| **视觉维度** | 颜色、字体、圆角、阴影、背景、间距、图标风格 | ❌ 一律忽略 | ✅ 参考定制 |

- **默认（组件规范优先模式 Component-First Mode）**：上传的图片（原型图 / 设计图 / 截图 / wireframe / 手绘稿）只作为 **内容、功能、交互、数据字段** 的参考。图片中的**结构布局**（如筛选区上下排列、单列布局、分组方式）与**视觉样式**（颜色、字体、圆角、阴影、背景、间距、边框、图标风格）均**不采用**——页面结构与视觉一律按 Ant Design 默认规范实现。
- **仅当检测到指向性文案（视觉参考模式 Visual-Reference Mode）**：图片才同时作为 **结构布局 + 视觉** 参考，在 Ant Design 组件基础上采用图片布局并定制视觉。

**关键判定原则：**
> 图片的视觉与结构是否构成"设计明确要求"（第 1、6、12 节），由**模式**决定，而不是由图片本身决定。默认模式下，即使图片中的布局或视觉与 Ant Design 默认明显不同（例如筛选区上下布局、红色按钮、圆角卡片、自定义配色），也**不**构成实现依据，必须使用 Ant Design 默认结构与默认样式。

## 2.2 两种模式

### 模式 A：组件规范优先（Component-First Mode）— 默认
- **适用**：绝大多数情况——用户上传原型图/设计图/截图、或仅给出自然语言需求，且未明确要求参考视觉。
- **图片角色**：内容 + 功能 + 交互 + 数据字段参考；**结构布局与视觉零参考**。
- **实现策略**：
  1. 内容文案、功能交互、数据字段取自图片/需求；
  2. **页面结构与布局按 Ant Design 页面模式规范（第 12 节）重新组织**，不照搬原型图结构——上下布局、单列排列、分组方式、栅格分配、区域划分等结构样式一律不采用；
  3. 视觉一律 Ant Design 默认：默认蓝色主色（5.x `#1677ff` / 4.x `#1890ff`）、8px 间距网格、默认字号/字重/行高、默认圆角/边框/阴影、默认图标；
  4. **禁止**因图片视觉添加任何定制：禁止 `ConfigProvider` 主题覆盖、禁止自定义 `colorPrimary`、禁止硬编码颜色/圆角/阴影/背景、禁止引入非默认间距（除非需求**文字**明确指定具体尺寸）；
  5. 组件类型识别只依据**语义/功能/交互/上下文**（第 10 节），不依据外观——图片上控件长得像什么不影响组件选择。
- **示例 1（视觉）**：图片中出现红色按钮、圆角卡片、自定义配色 → 仍使用 Ant Design `Button type="primary"`（默认蓝）、`Card`（默认圆角/边框）、默认主题，不参考其视觉。
- **示例 2（结构）**：原型图中筛选区为"上面标题、下面一个选择框"的上下布局 → 默认模式改为 Ant Design 查询区规范：一行最多 3 个筛选/输入框的水平排布（见第 12 节），标题按页面标题层级置于页面顶部，不保留原型图的上下结构。

### 模式 B：视觉参考（Visual-Reference Mode）— 仅当明确触发
- **适用**：检测到指向性文案（见 2.3），用户明确要求参考图片（设计稿/高保真 UI 图）的布局与视觉。
- **图片角色**：内容 + 功能 + 交互 + 数据字段 + **结构布局** + **视觉** 参考。
- **实现策略**：
  1. 页面**结构/布局按图片所示采用**（设计稿/高保真图的区域划分、排布方式、分组方式被保留）；
  2. 仍以 Ant Design 组件为唯一实现基础（不得因视觉差异换成自定义组件，见第 4、6 节）；
  3. 视觉差异通过 Ant Design 官方机制定制（5.x `ConfigProvider theme.token` / 官方组件 prop / 4.x less 变量），禁止裸 CSS 硬编码；
  4. 仅定制图片中 **明确可见且与 Ant Design 默认不同** 的视觉属性；其余保持默认。

## 2.3 判定规则（何时启用视觉参考）
按以下顺序判定，**取第一个命中的结论**：

### STEP 1 — 扫描用户自然语言指令（最高优先级）
扫描本轮指令及对话上下文中是否出现：
- **视觉参考触发词**（出现任一 → 视觉参考模式）：
  - 中文：`设计稿`、`设计图`、`视觉稿`、`视觉设计`、`高保真`、`视觉还原`、`还原设计`、`按图样式`、`参考此图`、`按图片的视觉`、`按图配色`、`用图上的颜色`、`保持图片风格`、`照着这张图`、`按这个设计做` 等明确指向"参考视觉"的表述。
  - 英文：`design spec`、`visual design`、`high-fidelity`、`hi-fi`、`mockup`、`style reference`、`match the design`、`follow the visual`、`keep the look` 等。
- **强制组件规范词**（出现任一 → 强制组件规范优先，**优先级高于触发词**）：
  - 中文：`用默认样式`、`组件库规范`、`用 antd 默认`、`默认组件样式`、`不要参考配色`、`忽略图片视觉`、`不按图样式`、`用标准组件` 等。
  - 英文：`use default`、`antd default`、`default style`、`ignore the visual`、`use component defaults` 等。

> 反向示例（均 → 组件规范优先）：
> - "按这个原型做个页面" → 组件规范优先（"原型"不含视觉参考指向）
> - "把这张图做成页面" / "帮我实现这个需求" → 组件规范优先
> - "照着这张**设计稿**的样式做" → 视觉参考模式（出现触发词"设计稿"）

### STEP 2 — 无触发词时（默认）
- 用户指令无任何触发词 → **组件规范优先**。**即使上传的是高保真设计图，也不参考其视觉。**
- 图片文件名 / 图片内文字含 `设计稿`、`设计图`、`hi-fi`、`mockup` 等标识：仅作**辅助信号**，用于提高对"视觉参考意图"的敏感度，但**不单独触发**视觉参考模式，仍以用户指令为准（保守默认）。

### STEP 3 — 兜底
- 任何无法判定 / 判据不足的情况 → **组件规范优先**。

## 2.4 模式声明（便于设计验证）
每次实现都必须在交付物中显式声明当前模式，例如代码顶部注释：
```tsx
// Visual Mode: Component-First (default) — 图片仅作内容/功能参考；结构与视觉均采用 Ant Design 默认规范
// Visual Mode: Visual-Reference — 已按图片布局与视觉定制（触发依据：指令含"设计稿/高保真"）
```
该声明用于设计验证阶段快速定位"是否误参考了图片的视觉或结构"，也是第 25 节模式一致性验证的依据。

---
# 3. Non-Negotiable Ant Design First Rule
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
**Core rule: Use the MINIMUM default props. Do NOT add any prop that changes Ant Design's default layout or visual structure. Only add props when the design explicitly requires a deviation from default.**
If a default visual element (divider, border, spacing, icon) is missing, you omitted a required prop — fix the prop, do NOT patch with custom CSS.
---
**Modal**
Ant Design Modal default structure (rendered automatically when props are correct):
- Header: `title` + close button + bottom divider line
- Body: your content
- Footer: `Cancel` (left) + `OK` (right, primary) + top divider line (full-width)
**Minimum required props — all three MUST be present:**
- `title` — without it, no header and no header divider
- `onOk` — without it, no footer button and no footer divider
- `onCancel` — without it, no footer button and no footer divider
**Template (copy exactly, do not add/remove props):**
```tsx
<Modal
  title="标题"
  open={visible}
  onOk={handleOk}
  onCancel={() => setVisible(false)}
>
  内容
</Modal>
```
**Form in Modal (default horizontal layout — label left, input right):**
```tsx
<Modal title="编辑" open={visible} onOk={form.submit} onCancel={() => setVisible(false)}>
  <Form form={form} onFinish={handleSubmit}>
    <Form.Item name="name" label="名称" rules={[{ required: true }]}>
      <Input />
    </Form.Item>
  </Form>
</Modal>
```
**FORBIDDEN:**
- `footer={null}` — removes footer and its divider
- Custom `footer={...}` — only when design explicitly requires non-standard buttons
- Manual `<Divider />` inside body — Ant Design already renders dividers
- `layout="vertical"` on Form — changes default horizontal to vertical (label above input)
- `<div>` + z-index mock modal — always use `<Modal>`
- Percentage `width`
**Optional (only when needed):** `width` (fixed px), `okText`, `cancelText`, `destroyOnClose`, `maskClosable={false}`.
**Drawer:** same rules + `placement` ("right" default).
---
**Form**
Default layout is **horizontal** (label on left, input on right). Do NOT add `layout="vertical"`.
**Template:**
```tsx
<Form onFinish={handleSubmit}>
  <Form.Item name="username" label="用户名" rules={[{ required: true }]}>
    <Input />
  </Form.Item>
  <Form.Item>
    <Button type="primary" htmlType="submit">提交</Button>
  </Form.Item>
</Form>
```
**Required:** every field wrapped in `<Form.Item name="xxx" label="xxx">`. Submit button has `htmlType="submit"`.
**Optional:** `labelCol={{ span: 6 }}` `wrapperCol={{ span: 18 }}` to control label/input width ratio.
**Use `Form.useForm()`** for `validateFields`, `setFieldsValue`, `resetFields`.
---
**Table**
**Template:**
```tsx
<Table
  columns={[
    { title: '名称', dataIndex: 'name', key: 'name' },
    { title: '操作', key: 'action', render: (_, r) => <Space><Button type="link">编辑</Button><Button type="link" danger>删除</Button></Space> },
  ]}
  dataSource={data}
  rowKey="id"
/>
```
**Required:** `columns` (each with `title`, `dataIndex`, `key`), `dataSource`, `rowKey`.
**Default:** pagination is bottom-right. Use `pagination={false}` to hide. `scroll={{ x: 'max-content' }}` for horizontal overflow.
---
**Select / Radio.Group / Checkbox.Group**
All are controlled: `value` + `onChange`.
```tsx
<Select value={val} onChange={setVal} options={[{ label: 'A', value: 1 }, { label: 'B', value: 2 }]} />
<Radio.Group value={val} onChange={e => setVal(e.target.value)}>
  <Radio value={1}>A</Radio>
  <Radio value={2}>B</Radio>
</Radio.Group>
<Checkbox.Group value={vals} onChange={setVals} options={[{ label: 'A', value: 1 }, { label: 'B', value: 2 }]} />
```
---
**Button**
`type="primary"` (main) / `default` (secondary) / `dashed` / `text` / `link`. `danger` for destructive. `loading` for async. Group with `<Space>`.
---
# 4. Ant Design Is the UI Foundation
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
# 5. Design Is Not the Component Library
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

> **模式前提：** 本节"设计提供视觉参考"仅在「视觉参考模式」（第 2 节）下成立。在默认的「组件规范优先模式」下，设计/图片只提供结构、内容、功能、交互与层级，**不提供**颜色、字体、圆角、阴影等视觉定制依据。
---
# 6. Visual Customization
**模式前提：本节视觉定制仅适用于「视觉参考模式」（第 2 节）。在「组件规范优先模式」下禁止任何视觉定制——一律使用 Ant Design 默认样式，图片中的视觉差异不构成定制依据。**

**DEFAULT FIRST. Use Ant Design's default visual style (blue theme, default spacing, default typography) unless the design explicitly specifies something different.**
Do NOT proactively change colors, fonts, spacing, or theme. Do NOT add `ConfigProvider` with custom theme tokens. Do NOT set `@primary-color` or `colorPrimary` to a custom value.
Only customize when the design clearly shows a different value. In that case:
> **Component identity comes from Ant Design.**
>
> **Visual differences come from the design, applied via Ant Design's official theming / Design Token mechanism.**
```text
Ant Design component (default blue)
+
design-specific token override (only if design differs from default)
=
final implementation
```
Never hardcode raw CSS values. Use official props or Design Tokens.
Official design spec: https://ant.design/docs/spec/values
---
# 7. Ant Design Version
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

> **版本一致性说明：** 本 Skill 所有参考文档（`core/*.md`、`components/*.md`）中提到的 "Ant Design" 一律指**项目实际检测到的 Ant Design 版本**，不默认任何特定大版本；文档中的 `4.x / 5.x / 6.x` 对照仅为**不同版本的 API / Token 差异参考**，实际实现时按检测到的版本选择对应写法。无项目 / 无 Ant Design 依赖时，默认使用最新稳定版（见本节末尾）。
>
> 参考文档中的官方文档链接均指向 `ant.design`（对应实际版本），不再锁定 `4x.ant.design`。
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
# 8. Ant Design API Is Authoritative
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
# 9. Components That Do Not Exist in Ant Design
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
# 10. Component Recognition
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

> **模式前提：** 组件类型识别始终基于**语义目的/交互/内容/上下文/状态**，**不基于外观**（外观识别只可能导致误选组件）。在「组件规范优先模式」下尤其如此——图片上控件的颜色、圆角、形状装饰均不参与组件类型判定。
---
# 11. Composite Components
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
# 12. Page Structure
## 12.1 结构识别
Analyze the design before implementation.
Identify（从图片/需求中识别页面包含哪些内容区域与元素）:
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

## 12.2 结构生成规则（Structure Generation）
**结构由"内容清单 × Ant Design 页面模式规范"决定，不由图片布局决定。**

- **组件规范优先模式（默认）**：
  1. 先从图片/需求中提取**内容清单**——页面包含哪些字段、筛选条件、操作按钮、数据区、状态等；
  2. 依据内容清单匹配页面模式（List / Detail / Form / Dashboard 等，见 `core/page-patterns.md`）；
  3. 按 Ant Design 标准页面结构（见 12.3）与页面模式模板组织布局；
  4. **不采用**原型图中的结构样式——上下布局、单列排列、分组方式、栅格分配、区域划分、元素的相对位置等均不照搬。
- **视觉参考模式（仅触发）**：结构/布局按图片所示采用（设计稿/高保真 UI 图的排布被保留），但组件仍用 Ant Design。

## 12.3 Ant Design 标准页面结构规范
默认模式下，按以下 Ant Design 通用结构生成（各页面模式的具体模板见 `core/page-patterns.md`）：

```text
页面顶部
├── Breadcrumb 面包屑
├── Typography.Title 页面标题
│
查询区（表格/列表上方，Ant Design 查询表单规范）
├── Form 组织筛选条件
├── 一行最多 3 个筛选/输入框（第 12.3.1 条，强制）
├── 超过 3 个自动换行，每行最多 3 个
├── 末尾：查询(primary) + 重置(default) 按钮
│
操作区（表格右上角 / 查询区同行右侧）
├── 新增(primary)、导入、导出、批量删除(danger) 等主操作
│
数据区
├── Table 主体（含分页，默认右下角）
│
弹层
├── Modal / Drawer 承载新增、编辑、详情等
```

### 12.3.1 查询区布局（强制规则）
> **表格/列表上方的查询区，一行最多展示 3 个筛选/输入框。**
- 筛选/输入框数量 ≤ 3 → 全部放在同一行；
- 数量 > 3 → 自动换行，**每行最多 3 个**；
- 查询、重置按钮紧跟在最后一个筛选项之后（可同行末尾或另起一行，视剩余空间）；
- 用 Ant Design `Form`（`layout="inline"` 或 grid 布局）组织筛选条件，不使用自定义 div 手工拼排。

示例（3 个筛选项 → 一行；5 个筛选项 → 两行，第一行 3 个、第二行 2 个 + 按钮）：
```text
[供应商名称____] [状态 ▼] [类型 ▼]     [查询][重置]      ← 3 个，一行
[供应商名称____] [状态 ▼] [类型 ▼]                       ← 第 1 行（3 个）
[创建时间____]   [负责人 ▼]        [查询][重置]           ← 第 2 行（2 个 + 按钮）
```
- 此规则同样适用于筛选条件由**原型图**提供的情况：原型图若把筛选项画成"上下单列"，默认模式一律改为上述水平多列规范；仅视觉参考模式（设计稿/高保真）保留图片布局。

Then construct the page primarily from Ant Design components.
---
# 13. Layout
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

**模式前提（见第 2、12 节）：** 默认组件规范优先模式下，布局按 Ant Design 页面结构规范（第 12.3 节）组织，**不照搬原型图的排布方式**（上下/左右、单列、分组等）。仅视觉参考模式下才采用图片的布局结构。
---
# 14. Interaction
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
# 15. States
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
# 16. Colors
**模式前提：在「组件规范优先模式」下禁止任何颜色定制（不得使用 ConfigProvider 主题、不得自定义 colorPrimary），一律使用 Ant Design 默认蓝色主题。仅「视觉参考模式」可参考设计稿颜色并映射至官方 token。**

**DEFAULT: Ant Design blue theme (#1677ff in 5.x, #1890ff in 4.x). Do NOT change primary color unless the design explicitly specifies a different brand color.**
Do NOT add `ConfigProvider` with custom `theme.token.colorPrimary`. Do NOT set `@primary-color` to a custom value. Do NOT add global theme configuration.
Only when the design explicitly shows a different primary color, map it to the correct token:
| Design role | Ant Design 4.x | Ant Design 5.x |
|---|---|---|
| 主色 / primary | `@primary-color` | `colorPrimary` |
| 成功 / success | `@success-color` | `colorSuccess` |
| 警告 / warning | `@warning-color` | `colorWarning` |
| 错误 / error | `@error-color` | `colorError` |
| 信息 / info | `@info-color` | `colorInfo` |
Apply via `ConfigProvider` (5.x: `theme.token`, 4.x: less variables). Only override tokens that differ from default. Never hardcode hex values in component styles.
---
# 17. Typography
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

> **模式前提：** 排版定制（字号/字重/行高等非默认值）同样仅在「视觉参考模式」下允许。默认模式下使用 Ant Design 默认排版阶梯。
---
# 18. Spacing and Dimensions
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

> **模式前提：** 尺寸与间距的"设计值"仅在「视觉参考模式」下从图片提取；「组件规范优先模式」下间距一律使用 Ant Design 默认 8px 网格，除非需求**文字**明确给出具体尺寸。
---
# 19. Icons
When an appropriate Ant Design icon exists:
**use the Ant Design icon.**
If no suitable icon exists:
* use an existing project icon;
* use the provided design asset;
* or implement an appropriate custom icon.
Do not substitute emoji for interface icons.
---
# 20. Existing Project
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
# 21. Other UI Libraries
If the project already uses another UI library:
Do not automatically rewrite the entire project.
If the user explicitly requests Ant Design:
implement the requested page using Ant Design while minimizing unnecessary architectural changes.
Do not mix multiple UI libraries for the same standard component without a clear reason.
---
# 22. Responsive Design
If multiple design breakpoints are provided:
implement the corresponding responsive behavior.
If only one viewport is provided:
preserve the supplied design exactly at that viewport and infer reasonable responsive behavior for other sizes without redesigning the page.
---
# 23. Accessibility
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
# 24. Code Quality
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
# 25. Validation — Ant Design First
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
### Mode validation（模式一致性验证 — 核心防视觉/结构干扰检查）
先确认本次实现处于哪个模式（见第 2 节 2.4 模式声明）：
```text
组件规范优先模式（默认）→
  - 检查产物是否残留输入图片的视觉属性：
      非默认颜色 / 自定义圆角 / 自定义阴影 / 自定义背景 / 自定义字体 /
      非 8px 网格间距 / 图片上的图标风格 / 图片装饰形状
  - 检查是否因图片视觉添加了 ConfigProvider 主题 / colorPrimary 覆盖 / 硬编码色值
  - 检查产物是否残留输入图片的结构布局：
      上下单列排布 / 非规范分组 / 筛选区每行超过 3 个 / 区域划分照搬原型图
  - 检查查询区是否遵循"一行最多 3 个筛选/输入框"（第 12.3.1 节）
  - 如有任一残留 → 移除，恢复 Ant Design 默认结构（第 12.3 节）与默认样式
视觉参考模式 → 逐个检查：
  - 每个视觉定制是否有明确的图片依据
  - 是否通过官方 Token / 官方 prop 实现（非裸 CSS 硬编码）
  - 是否仍以 Ant Design 组件为基础（未换自定义组件）
  - 结构/布局是否按图片采用（组件规范优先模式下不出现图片布局）
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
> **模式前提：** 视觉一致性校验目标取决于模式——组件规范优先模式下，校验目标是"与 Ant Design 默认规范一致"，而非"与图片一致"；视觉参考模式下才校验"与图片视觉一致"。
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
# 26. Priority Rules
When rules conflict, use this priority:
```text
0. Visual Mode (Component-First by default, 第 2 节)
1. Existing project architecture
2. Ant Design component system
3. Ant Design version/API compatibility
4. Design functionality
5. Design visual requirements（仅在视觉参考模式下生效）
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
# 27. User Interaction
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

**视觉模式如何由用户控制：**
- 默认（无需说明）：上传原型图/设计图/截图 → 组件规范优先，使用 Ant Design 默认样式生成页面，不参考图片视觉。
- 需要参考视觉时，在指令中明确包含指向性文案，例如：
  - "**照着这张设计稿的样式**做"
  - "参考这张**设计图**的配色和风格"
  - "按**高保真**视觉还原"
- 需要切回组件规范时：
  - "用**默认组件样式**，不要参考图片"
  - "忽略图片视觉，按 **antd 默认** 实现"
- 若一开始未触发视觉参考、但用户希望参考图片视觉，直接补充说明即可，无需重新上传。
---
# 28. Final Execution Algorithm
For every Design-to-Code task:
```text
INPUT
Design / Prototype / Screenshot / Figma / Requirement
↓
0. Perform Visual Mode Detection（第 2 节）
   ├─ 含视觉参考触发词 → Visual-Reference Mode
   └─ 默认（无触发词 / 有强制组件规范词）→ Component-First Mode
   └─ 记录模式并写入模式声明（2.4）
1. Inspect project
2. Detect installed Ant Design version
   ├─ If project exists → use its installed antd version
   └─ If no project (pure Figma / screenshot / prototype) → default to React + TypeScript + latest stable Ant Design, MUST import from 'antd'
3. Understand page structure
   ├─ Component-First Mode → 提取内容清单（字段/操作/数据区），匹配页面模式（page-patterns），结构按第 12.3 节规范组织，不照搬原型图布局
   └─ Visual-Reference Mode → 结构/布局按图片所示采用
4. Identify page functionality
5. Identify UI elements
6. Cross-check EVERY identified element against the Mandatory Component Mapping Table (Section 3) — if it's in the table, the mapped Ant Design component is NON-NEGOTIABLE
7. Determine semantic purpose
8. Check whether Ant Design provides an appropriate component
9. If YES → MUST use Ant Design
10. If NO → custom implementation allowed
11. Verify official API for the project version
12. Build page using Ant Design as the foundation
13. Apply visual styling per Visual Mode（第 2 节）
    ├─ Component-First Mode → 使用 Ant Design 默认样式，忽略图片视觉（不添加任何主题/颜色/圆角/阴影定制）
    └─ Visual-Reference Mode → 仅定制图片中明确可见且与默认不同的视觉属性（经官方 Token / prop）
14. Implement required interaction
15. Validate component usage
16. Validate API/version
17. Validate mode consistency（第 25 节 Mode validation，含结构与视觉一致性）
18. Validate visual & structural fidelity per mode（组件规范优先 → 与 Ant Design 默认一致；视觉参考 → 与图片一致）
19. Validate interaction
20. Validate code
21. Deliver final implementation（含模式声明）
```
---
# 29. Ultimate Rule
**Ant Design First.**
If Ant Design has the component:
> **Use Ant Design.**
If Ant Design does not have the component:
> **Build it yourself.**
If the Ant Design component does not visually match the design:
> **Customize the Ant Design component. Do not replace it unnecessarily.**

**Visual Mode First（视觉模式优先）：** 默认组件规范优先，图片视觉不参与实现；仅当识别到「设计稿/设计图」等指向性文案时，才参考图片视觉。模式判定（第 2 节）优先于一切视觉决策。

The goal is not to make a page that merely looks like Ant Design.
The goal is to build the page **with Ant Design as its foundational UI component system**, while using the supplied design as the source of content, layout, visual customization, and interaction requirements.
---
# 30. Reference Files
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
