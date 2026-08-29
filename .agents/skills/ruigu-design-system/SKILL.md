---

name: ruigu-design-system
description: Ant Design First Design-to-Code skill. Build pages primarily and systematically with the project's installed Ant Design component library. Analyze designs, prototypes, screenshots, Figma files, and natural-language requirements to determine page structure, functionality, and visual requirements, then implement the page using Ant Design components as the foundational UI system. When an appropriate Ant Design component exists, it MUST be used rather than recreated with native HTML or custom UI. Only elements that have no suitable Ant Design equivalent may be custom implemented. Design references control content, layout, and visual customization; Ant Design controls the foundational component system and implementation conventions.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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

Apply them through the appropriate project/version-supported Ant Design theming or component styling mechanism.

Do not globally modify the entire Ant Design theme merely to reproduce one component.

Prefer the smallest appropriate scope.

---

# 16. Typography

Preserve the design's:

* font family
* font size
* font weight
* line height
* letter spacing
* hierarchy

Use Ant Design Typography where appropriate.

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
3. Understand page structure
4. Identify page functionality
5. Identify UI elements
6. Determine semantic purpose
7. Check whether Ant Design provides an appropriate component
8. If YES → MUST use Ant Design
9. If NO → custom implementation allowed
10. Verify official API for the project version
11. Build page using Ant Design as the foundation
12. Apply design-specific visual styling
13. Implement required interaction
14. Validate component usage
15. Validate API/version
16. Validate visual fidelity
17. Validate interaction
18. Validate code
19. Deliver final implementation
```

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
