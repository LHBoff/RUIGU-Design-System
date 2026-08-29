---
---
name: ruigu-design-system
description: Design-to-Code skill for converting UI designs, prototypes, screenshots, Figma designs, and natural-language requirements into production-ready interfaces. Automatically identifies UI structure, determines which elements correspond to Ant Design components, detects the project's actual Ant Design version, uses the matching official Ant Design component and API when available, and lets the Agent implement elements that have no suitable Ant Design equivalent. Design visuals remain the source of truth for styling.
---

# RUIGU Design System

## 1. Mission

RUIGU is a **Design-to-Code execution skill**.

Its job is:

**Design / Prototype / Screenshot / Figma / Requirement → UI Understanding → Component Decision → Ant Design Implementation → Visual Styling → Interaction → Code → Validation**

RUIGU does **not** replace Ant Design.

RUIGU does **not** create a second UI component library.

RUIGU does **not** maintain duplicated Button/Input/Select/Table APIs.

RUIGU uses the official Ant Design ecosystem as the authoritative source for components and APIs whenever a suitable Ant Design component exists.

---

# 2. Core Principle

The following rules are mandatory.

## Rule 1 — Ant Design is the component standard

When the target project uses Ant Design and the design contains an element that can be represented by an Ant Design component:

**Use the corresponding Ant Design component.**

Do not replace an existing Ant Design component with:

* native HTML controls
* another UI component library
* an unnecessary custom component
* a visually similar hand-built component

Examples:

* Button → Ant Design Button
* Input → Ant Design Input
* Search input → Ant Design Input.Search when appropriate
* Select → Ant Design Select
* Date selector → Ant Design DatePicker / RangePicker
* Table → Ant Design Table
* Form → Ant Design Form
* Modal → Ant Design Modal
* Drawer → Ant Design Drawer
* Tabs → Ant Design Tabs
* Pagination → Ant Design Pagination
* Tag → Ant Design Tag
* Badge → Ant Design Badge
* Tooltip → Ant Design Tooltip
* Dropdown → Ant Design Dropdown
* Upload → Ant Design Upload
* Progress → Ant Design Progress
* Spin → Ant Design Spin
* Empty → Ant Design Empty
* Result → Ant Design Result
* Alert → Ant Design Alert
* Card → Ant Design Card
* Descriptions → Ant Design Descriptions
* Statistic → Ant Design Statistic
* Steps → Ant Design Steps
* Breadcrumb → Ant Design Breadcrumb
* Menu → Ant Design Menu
* Checkbox → Ant Design Checkbox
* Radio → Ant Design Radio
* Switch → Ant Design Switch
* Slider → Ant Design Slider
* AutoComplete → Ant Design AutoComplete
* Cascader → Ant Design Cascader
* TreeSelect → Ant Design TreeSelect
* Tree → Ant Design Tree
* List → Ant Design List
* Avatar → Ant Design Avatar
* Image → Ant Design Image
* Calendar → Ant Design Calendar

This list is illustrative, not exhaustive.

Always check the actual Ant Design documentation for the available component.

---

# 3. Ant Design Version Policy

Never assume a fixed Ant Design major version.

The project version is authoritative.

## Version detection order

Before generating Ant Design code:

1. Inspect `package.json`.
2. Inspect the installed dependency if available.
3. Determine the actual `antd` major version.
4. Use the API and implementation conventions corresponding to that version.

Examples:

```text
antd 4.x → use Ant Design 4.x API
antd 5.x → use Ant Design 5.x API
antd 6.x → use Ant Design 6.x API
```

Do not mix APIs across major versions.

Do not silently upgrade or downgrade Ant Design.

If the project does not specify an Ant Design version:

* use the current official Ant Design documentation available to the environment;
* if installation is required, use the project's existing dependency policy;
* do not invent version-specific APIs.

Official Ant Design source:

https://ant.design/

Official React documentation:

https://ant.design/docs/react/introduce/

Official component documentation:

https://ant.design/components/

---

# 4. Ant Design Is the Source of Component Truth

Do not reproduce Ant Design component APIs inside this Skill.

Do not maintain independent API definitions such as:

```text
button-api.md
input-api.md
select-api.md
table-api.md
```

as authoritative sources.

The official Ant Design documentation is the authoritative source for:

* component availability
* component API
* props
* events
* supported states
* composition
* accessibility behavior
* theme behavior
* version-specific differences

When uncertain about an API:

**consult the official Ant Design documentation instead of guessing.**

Never invent:

* props
* component names
* events
* hooks
* methods
* tokens
* internal APIs

Use documented public APIs.

---

# 5. Design Is the Visual Source of Truth

The design, prototype, screenshot, Figma file, or supplied visual reference is the primary source of truth for appearance.

When an Ant Design component is used, its implementation must be adapted to match the design.

Extract and preserve, where visually available:

* background colors
* text colors
* primary colors
* secondary colors
* border colors
* divider colors
* typography
* font family
* font size
* font weight
* line height
* letter spacing
* width
* height
* padding
* margin
* gap
* border radius
* border width
* border style
* shadows
* opacity
* icon size
* icon position
* alignment
* component density
* hover state
* active state
* focus state
* disabled state
* selected state
* error state
* warning state
* success state
* loading state

Do not substitute Ant Design's default visual appearance when the design clearly specifies a different appearance.

---

# 6. Component Structure vs Visual Styling

Separate these two decisions.

## Component structure

Determined by:

**Ant Design**

Example:

```text
Design element
→ Button
→ Ant Design Button
```

## Visual appearance

Determined by:

**Design**

Example:

```text
Ant Design Button
+
design background color
+
design text color
+
design height
+
design radius
+
design typography
```

Therefore:

**Ant Design determines what the component is.**

**The design determines what that component should look like.**

Do not confuse these responsibilities.

---

# 7. When No Ant Design Component Exists

If the design contains an element for which there is no appropriate Ant Design component:

**do not force it into an unrelated Ant Design component.**

Instead:

1. Confirm that no suitable Ant Design component exists.
2. Implement the element using the Agent's normal frontend capabilities.
3. Reproduce the design as accurately as possible.
4. Reuse Ant Design components internally where they are genuinely applicable.
5. Do not falsely label the custom implementation as an Ant Design component.

Example:

```text
Design element
→ no suitable Ant Design component
→ custom React component
→ custom CSS / appropriate implementation
```

The absence of an Ant Design equivalent is an explicit exception to the Ant Design component requirement.

---

# 8. Custom Components Must Not Be Forced Into Ant Design

Do not use an unrelated Ant Design component merely because it looks similar.

Bad:

```text
Custom visualization
→ force into Table
```

Bad:

```text
Custom navigation
→ force into Menu
```

Bad:

```text
Custom editor
→ force into Input
```

Correct:

```text
No suitable Ant Design component
→ custom implementation
```

However, if part of the custom component contains standard controls, use Ant Design for those controls.

Example:

```text
Custom advanced filter panel
├── Ant Design Input
├── Ant Design Select
├── Ant Design DatePicker
└── custom filter visualization
```

---

# 9. Design-to-Code Analysis Process

Before generating code, perform the following analysis internally.

## Step 1 — Understand the page

Identify:

* page type
* primary purpose
* major sections
* hierarchy
* navigation
* content areas
* actions
* forms
* tables
* dialogs
* overlays
* responsive regions

Do not generate code before understanding the page structure.

---

## Step 2 — Identify UI regions

Break the design into meaningful regions.

Examples:

```text
Page
├── Header
├── Toolbar
│   ├── Search
│   ├── Filters
│   └── Actions
├── Content
│   └── Table
└── Pagination
```

or:

```text
Page
├── Sidebar
├── Header
└── Main
    ├── PageHeader
    ├── Form
    └── ActionArea
```

---

# 10. Component Recognition

For every visible UI element:

1. Identify its semantic purpose.
2. Identify its interaction behavior.
3. Identify its visual appearance.
4. Determine whether an Ant Design component represents it.
5. If yes, use that component.
6. If no, use a custom implementation.

Do not identify components solely by visual shape.

Use:

* position
* surrounding elements
* text
* interaction
* state
* semantic purpose
* repeated patterns

to determine the correct component.

---

# 11. Composite Component Recognition

Do not assume one visual region equals one component.

A single design region may correspond to multiple Ant Design components.

Example:

```text
Filter bar
→ Form
   ├── Form.Item
   │   └── Input
   ├── Form.Item
   │   └── Select
   ├── Form.Item
   │   └── DatePicker
   └── Button
```

Another example:

```text
Search
→ Input.Search
```

instead of:

```text
Input + manually constructed search button
```

when `Input.Search` correctly represents the intended behavior.

---

# 12. Layout Recognition

Use the appropriate Ant Design layout primitives when applicable.

Prefer:

* Layout
* Row
* Col
* Space
* Grid
* Flex
* Divider

according to the actual project version and available APIs.

Do not create unnecessary layout components.

Do not use arbitrary absolute positioning when the design can be accurately reproduced with normal layout systems.

Absolute positioning is allowed when it is genuinely required by the design.

---

# 13. Typography

Preserve the design's typography.

Identify:

* heading hierarchy
* body text
* secondary text
* labels
* helper text
* captions
* numeric text
* links
* emphasis

Use Ant Design Typography where appropriate.

Do not replace all typography with arbitrary `<div>` or `<span>` elements when an appropriate Ant Design typography component exists.

However, do not force Typography components where plain text is more appropriate.

---

# 14. Color Handling

Color is part of visual fidelity.

For every Ant Design component visible in the design:

1. identify its intended color;
2. determine whether the current Ant Design version provides an appropriate public theme/token/API mechanism;
3. use that mechanism when appropriate;
4. otherwise use scoped styling;
5. preserve the design color.

Do not blindly use Ant Design default colors.

Do not invent colors.

Do not approximate a clearly identifiable color unnecessarily.

Do not globally change Ant Design colors merely to match one isolated component.

Use the smallest appropriate scope:

```text
global theme
→ page-level token
→ component-level style
→ state-specific style
```

according to the project architecture.

---

# 15. Spacing and Dimensions

Preserve meaningful dimensions from the design.

Pay attention to:

* component height
* row height
* column width
* container width
* padding
* gaps
* margins
* alignment
* vertical rhythm

Do not normalize all dimensions to arbitrary defaults if the design clearly specifies different values.

At the same time, do not hardcode every pixel unnecessarily when the design clearly represents a reusable spacing system.

Infer reusable spacing relationships when appropriate.

---

# 16. States

Identify component states shown or implied by the design.

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
expanded
collapsed
checked
unchecked
open
closed
```

If the design shows a state, reproduce it.

If the interaction logically requires a state that is not visually shown, implement the behavior using the corresponding Ant Design API when available.

Do not invent unnecessary states.

---

# 17. Interaction

Do not generate static screenshots disguised as applications.

When the design implies interaction, implement the interaction.

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
→ sorting / filtering / pagination when shown or required

Modal
→ open / close

Drawer
→ open / close

Tabs
→ active tab state

Dropdown
→ menu interaction

Upload
→ upload interaction when required
```

Use the project's existing architecture and Ant Design's official public APIs.

---

# 18. Existing Project Architecture

When generating code inside an existing project:

1. inspect the existing architecture;
2. reuse existing components where appropriate;
3. preserve existing routing;
4. preserve existing state management;
5. preserve existing styling conventions;
6. preserve existing package versions;
7. avoid unnecessary dependency changes.

Do not rewrite the entire application merely to implement one page.

Do not introduce a new UI framework if Ant Design is already present.

---

# 19. New Project / Empty Environment

When no existing application exists:

Use a conventional React implementation compatible with the environment.

If Ant Design is required:

```bash
npm install antd
```

Use the package version appropriate to the environment and project constraints.

Prefer modular imports and the project's established build system.

Do not add unrelated dependencies.

---

# 20. React and TypeScript

When the target is a React application:

* use React components;
* use TypeScript when the project uses TypeScript;
* use semantic component structure;
* use typed props;
* avoid unnecessary `any`;
* keep components maintainable;
* keep business logic separate from presentation when appropriate.

Use:

```tsx
import { Button } from 'antd';
```

rather than recreating the Button.

---

# 21. Icons

When the design uses an icon:

1. determine whether an Ant Design icon exists;
2. use the corresponding official icon when appropriate;
3. preserve icon size and visual placement;
4. if no suitable Ant Design icon exists, use an appropriate project-approved icon or custom asset.

Do not substitute arbitrary emoji for interface icons.

Do not use unrelated icons merely because they are available.

---

# 22. Accessibility

Preserve accessible behavior.

Use:

* semantic labels
* appropriate form labels
* keyboard interaction
* focus behavior
* accessible names
* meaningful button text
* appropriate disabled states

Do not sacrifice accessibility merely to reproduce a visual appearance.

---

# 23. Responsive Behavior

If the design includes multiple breakpoints or responsive references:

implement the responsive behavior.

If only one desktop design is provided:

infer reasonable responsive behavior without changing the intended desktop appearance.

Use the project's existing responsive architecture.

Do not invent elaborate responsive behavior that the design does not imply.

---

# 24. Do Not Overwrite the Design

Do not:

* redesign the page;
* modernize the UI without instruction;
* change colors for aesthetic reasons;
* replace components because another component seems prettier;
* add gradients without evidence;
* add shadows without evidence;
* add animations without evidence;
* change spacing without evidence;
* change typography without evidence.

The task is implementation, not redesign.

---

# 25. Design Fidelity Priority

When implementing an Ant Design component, preserve the following in order:

1. semantic component identity;
2. required interaction;
3. visual structure;
4. color;
5. dimensions;
6. spacing;
7. typography;
8. border;
9. radius;
10. shadow;
11. state appearance;
12. micro-details.

Do not sacrifice component identity merely to obtain superficial pixel similarity.

---

# 26. Ant Design Component Decision

For each significant design element, internally make this decision:

```text
What is this element?

        ↓

Does Ant Design provide an appropriate component?

        ↓

YES
→ use Ant Design

NO
→ implement custom

        ↓

If Ant Design:
→ determine project version
→ verify official API
→ implement component
→ apply design-specific visual styling

If custom:
→ implement normally
→ match design
→ reuse Ant Design subcomponents where appropriate
```

---

# 27. API Verification

Before using an unfamiliar Ant Design API:

* verify that the component exists;
* verify the API exists in the project's version;
* verify prop names;
* verify event names;
* verify value types;
* verify composition rules.

Never fabricate an API based on memory.

Never use undocumented internal APIs when a documented public API exists.

---

# 28. Validation

After generating the page, perform a self-check.

## Component validation

Check:

* every obvious Ant Design-compatible element uses Ant Design;
* no unnecessary custom replacement exists;
* no unrelated Ant Design component was forced into use;
* custom elements are genuinely unsupported or materially different.

## Version validation

Check:

* generated APIs match the project's installed Ant Design version;
* no cross-version APIs are mixed;
* no invented APIs exist.

## Visual validation

Check:

* colors
* typography
* spacing
* dimensions
* borders
* radius
* shadows
* alignment
* icons
* states

against the design.

## Interaction validation

Check:

* buttons work;
* inputs work;
* selects work;
* forms work;
* dialogs open and close;
* tabs switch;
* pagination works when required;
* filtering/sorting works when required;
* loading/error/disabled states work when required.

## Code validation

Check:

* imports are valid;
* components compile;
* TypeScript types are valid;
* no unnecessary dependencies were introduced;
* no placeholder components remain;
* no obvious runtime errors exist.

---

# 29. Output Requirements

When the user asks to generate a page:

Do the analysis internally.

Do not force the user to provide a component-by-component specification unless the design is genuinely ambiguous.

Return the implementation appropriate to the target environment.

If code is requested:

* provide complete usable code;
* include required imports;
* include required styles;
* include required supporting components;
* include required interaction logic;
* do not leave critical UI as pseudocode.

If a visual element cannot be confidently identified:

make the most reasonable interpretation based on surrounding context and the design rather than stopping unnecessarily.

---

# 30. User Prompt Requirements

The user should not need to repeat RUIGU's internal rules.

A normal request may be as simple as:

> Generate this page from the provided design.

or:

> Convert this design into a React page using RUIGU.

The Skill itself is responsible for:

* identifying components;
* checking Ant Design;
* checking the project version;
* verifying APIs;
* applying design styling;
* implementing interaction;
* validating the result.

Do not require the user to repeat these instructions.

---

# 31. Important Exceptions

## Exception A — No Ant Design equivalent

Use a custom implementation.

## Exception B — Existing project custom component

Reuse it when appropriate instead of unnecessarily replacing it.

## Exception C — Design explicitly requires a custom component

Implement the custom component.

## Exception D — Ant Design component exists but cannot reproduce a required behavior

Use Ant Design as the base where appropriate and extend it with custom logic/styling.

## Exception E — Project uses another UI framework

Do not silently replace the entire project's UI architecture.

Follow the existing project architecture unless the user explicitly requests migration to Ant Design.

---

# 32. Non-Negotiable Rules

The following rules override convenience:

### MUST

* inspect the project before generating;
* detect the actual Ant Design version;
* use Ant Design when an appropriate component exists;
* use official public APIs;
* use the design as visual truth;
* implement interactions represented by the design;
* validate the result.

### MUST NOT

* assume Ant Design 4.x;
* assume Ant Design 5.x;
* assume Ant Design 6.x;
* invent component APIs;
* mix major-version APIs;
* replace Ant Design components with native controls without reason;
* force unsupported designs into unrelated Ant Design components;
* require the user to manually describe every component;
* redesign the provided design;
* blindly apply Ant Design default colors when the design specifies different colors;
* depend on other RUIGU files for core execution.

---

# 33. Execution Summary

For every Design-to-Code task, follow this sequence:

```text
INPUT
Design / Prototype / Screenshot / Figma / Requirement

↓

1. Inspect project
2. Detect Ant Design version
3. Understand page structure
4. Identify UI regions
5. Identify semantic elements
6. Determine interaction
7. Match each element to Ant Design where appropriate
8. Verify official API for the project version
9. Identify design visual properties
10. Implement Ant Design components
11. Implement custom components only where necessary
12. Apply design-specific visual styling
13. Implement interaction
14. Validate component usage
15. Validate version/API correctness
16. Validate visual fidelity
17. Validate interaction
18. Validate code
19. Deliver the final implementation

OUTPUT
Production-ready page implementation
```

# 34. Final Principle

**RUIGU does not compete with Ant Design.**

Ant Design defines the components.

The project defines the installed version.

The design defines the visual result.

RUIGU connects the two.

Therefore:

**Design → Understand → Match Ant Design → Verify API → Implement → Style from Design → Validate.**

That is the complete RUIGU Design-to-Code workflow.
