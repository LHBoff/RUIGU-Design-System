---

name: ruigu-design-system
description: RUIGU Design System（锐锢中台组件库）是面向设计师、产品经理和开发者的 AI 设计与开发规范 Skill。基于 Ant Design 4.x 作为组件、API、交互和基础设计规范的权威底层标准；负责将中文、English、中文+English混合的自然语言需求识别为业务意图、页面模式和 Ant Design 组件，并在需要时生成符合规范的 UI 方案与 React + TypeScript + Ant Design 4.x 代码。Use when the user asks to design, review, select, explain, combine, or code UI components/pages, especially Button、Input、Select、Table、Card、Modal、列表页、详情页、表单页、Dashboard、中后台页面、设计规范或前端代码.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# RUIGU Design System

## 1. Identity

* Display name: RUIGU Design System
* 中文名称：锐锢中台组件库
* Version: 0.1.0
* Base design system: Ant Design 4.x
* Primary framework target: React + TypeScript + Ant Design 4.x
* Language: Chinese / English / mixed Chinese-English
* Audience: Designer / Product / Developer

RUIGU Design System does NOT replace or redefine Ant Design 4.x component APIs.

Ant Design 4.x is the authoritative source for component behavior, properties, visual variants, examples, and API details.

RUIGU adds an AI semantic and decision layer:

1. Understand user intent.
2. Normalize Chinese, English, and mixed-language component names.
3. Decide which component or pattern should be used.
4. Decide when components should be composed.
5. Apply business-semantic rules.
6. Map the decision to Ant Design 4.x.
7. When coding is requested, generate React + TypeScript + Ant Design 4.x code.

---

# 2. Source of Truth

For component implementation and API details, use the official Ant Design 4.x documentation.

Canonical component URLs:

* Button: https://4x.ant.design/components/button-cn/
* Input: https://4x.ant.design/components/input-cn/
* Select: https://4x.ant.design/components/select-cn/
* Table: https://4x.ant.design/components/table-cn/
* Card: https://4x.ant.design/components/card-cn/
* Modal: https://4x.ant.design/components/modal-cn/
* Component overview: https://4x.ant.design/components/overview-cn/

If a component is not yet represented by a local RUIGU component reference file, do not invent its API.

Use the official Ant Design 4.x documentation as the authority.

---

# 3. Language Understanding

Always normalize user language before making a component decision.

Examples:

* “增加一个按钮” -> Button
* “加一个 button” -> Button
* “Add a button” -> Button
* “增加一个 primary button” -> Button + type="primary"
* “增加一个主按钮” -> Button + type="primary"
* “加一个输入框” -> Input
* “加一个 input” -> Input
* “增加一个选择器” -> Select
* “加一个 select” -> Select
* “做一个表格” -> Table
* “add a table” -> Table
* “做一个卡片” -> Card
* “open a modal” -> Modal

Mixed-language recognition is mandatory.

Do not require the user to use the official English component name.

---

# 4. Decision Hierarchy

Use this order:

1. User intent / business goal
2. Page pattern
3. Component selection
4. Component variant / props
5. Component composition
6. Ant Design 4.x implementation
7. Code structure

Do not select a component solely because the user named it if the described business goal clearly requires a different component.

Example:

User says:

“做一个更多操作按钮”

If the intent is a menu of several secondary actions, prefer Dropdown / Dropdown.Button rather than creating many independent Buttons.

User says:

“让用户从多个供应商中选择一个”

Prefer Select, unless the number of options and context make Radio more appropriate.

---

# 5. Component Selection Rules

## Action

Use Button when the user needs to trigger an immediate action.

Typical semantic intents:

* 新增 / Add / Create
* 保存 / Save
* 提交 / Submit
* 确认 / Confirm
* 查询 / Search
* 重置 / Reset
* 编辑 / Edit
* 删除 / Delete
* 导出 / Export
* 上传 / Upload

## Input

Use Input when the user needs to enter free-form text.

## Select

Use Select when the user needs to choose from predefined options.

If there are fewer than about 5 options and the choices should be visible at once, consider Radio according to Ant Design guidance.

If the hierarchy is parent-child, consider Cascader.

## Table

Use Table for structured row-column data, especially when the page requires:

* sorting
* filtering
* pagination
* selection
* row actions

## Card

Use Card as a content container for grouped information, summaries, lists, images, or dashboard modules.

## Modal

Use Modal when the user must handle a task without leaving the current page and the interaction should be presented in a modal overlay.

For simple confirmation, use Modal.confirm or a lighter confirmation component when appropriate.

---

# 6. Business-Semantic Rules

## Primary action

An action that represents the main goal of an action area may use a primary Button.

An action area should generally have at most one primary Button.

## Destructive action

Delete / Remove / Destroy / Revoke / Disable-permanently / Modify-permission-type actions should be considered destructive.

Use Button with `danger` when a Button is appropriate.

For destructive actions that need confirmation, compose with Popconfirm or Modal.confirm according to complexity.

## Loading

For async actions, use the relevant Ant Design loading state.

For Button submission actions, prefer `loading` to prevent repeated submission while waiting.

## Disabled

Use `disabled` only when the action is genuinely unavailable.

When possible, explain why an important action is unavailable.

## Navigation

If the intent is navigation rather than an in-place action, prefer a link or navigation component instead of treating it as a generic action Button.

## More actions

If there are 3 or more secondary actions, consider grouping them into Dropdown / Dropdown.Button instead of rendering a long row of buttons.

---

# 7. Design Mode

When the user asks for UI design, respond with:

1. Page type / pattern
2. User goal
3. Component selection
4. Key interaction rules
5. States that must be considered
6. Optional component hierarchy
7. If useful, a concise wireframe-like structure

Do not over-explain Ant Design API unless the user asks for implementation.

---

# 8. Code Mode

When the user asks for code:

* Target React + TypeScript.
* Use Ant Design 4.x APIs.
* Prefer imports from `antd` and `@ant-design/icons` as appropriate.
* Do not use Ant Design 5.x-only APIs when targeting 4.x.
* Keep component names and props aligned with the official 4.x documentation.
* Include loading, empty, error, disabled, and permission-related states when the page requires them.
* Avoid inventing proprietary RUIGU component APIs unless such a component is explicitly documented in this Skill.

Default example:

```tsx
import { Button } from 'antd';

export default function Example() {
  return <Button type="primary">新增</Button>;
}
```

---

# 9. Review Mode

When asked to review a UI, check:

* Is the chosen component semantically appropriate?
* Is the action hierarchy clear?
* Is there more than one primary action in one action area?
* Are destructive actions clearly marked?
* Are confirmation requirements considered?
* Are loading and disabled states handled?
* Are tables overloaded with actions?
* Is Select being used where Radio/Cascader would be more appropriate?
* Are page patterns consistent?
* Does the implementation use Ant Design 4.x APIs?
* Are component props invented or inconsistent with the official documentation?

---

# 10. Reference Loading

Load only the relevant local reference files needed for the request.

Examples:

* Button request -> components/button.md
* Supplier management list -> patterns/list.md + components/table.md + components/button.md + components/input.md + components/select.md
* Detail page -> patterns/detail.md + relevant component references
* Form -> patterns/form.md + components/input.md + components/select.md + components/button.md
* Dashboard -> patterns/dashboard.md + components/card.md + relevant data-display components

Do not read every component reference for every request.

---

# 11. Output Principles

* Prefer clear, actionable answers.
* Use Chinese by default when the user writes Chinese.
* Preserve English component names in code and canonical mappings.
* When useful, show both:
  `中文语义 -> English canonical component`
* Do not claim a component is a RUIGU proprietary component unless it is explicitly documented as such.
* When official Ant Design behavior is relevant, defer to Ant Design 4.x.

---

# 12. Versioning

Current version: 0.1.0

Use Semantic Versioning:

* PATCH: bug fixes / wording / mapping corrections.
* MINOR: new components, patterns, or non-breaking AI capabilities.
* MAJOR: breaking rule changes or a base design-system migration.

GitHub is the recommended source of truth for RUIGU Design System source files.

---

# 13. Acceptance Tests

The Skill should correctly interpret:

1. 增加一个按钮
2. Add a button
3. 增加一个 primary button
4. 增加一个删除按钮
5. 加一个输入框
6. Add an input
7. 让用户选择供应商
8. 做一个供应商列表
9. 做一个供应商详情页
10. 生成 React + TypeScript + Ant Design 4.x 代码
11. 检查这个页面是否符合 RUIGU Design System

Expected behavior is semantic mapping first, implementation second.
