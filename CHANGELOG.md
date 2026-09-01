# Changelog

本仓库所有显著变更按时间倒序记录。

格式遵循 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/)，版本号遵循 [Semantic Versioning](https://semver.org/lang/zh-CN/)。

## [Unreleased]

### Added
- 新增「视觉模式判定」（Visual Mode Detection）：**默认组件规范优先**——上传图片仅作内容/功能参考，页面结构按 Ant Design 页面模式规范自行优化设计，视觉采用 Ant Design 默认规范；仅当检测到指向性文字（指令或图片置顶文字/标注，如「设计稿 / UI稿 / 设计图 / 高保真 / 视觉还原」）时才进入视觉参考模式，参考图片的结构布局与视觉样式后，再结合 Ant Design 组件搭建页面。
  - `SKILL.md` 新增第 2 节「Visual Mode — Component-First by Default」：内容/结构/视觉三维度判定表、模式 A（组件规范优先）/模式 B（视觉参考）、三步判定规则（指令触发词 → 图片指向性标注 → 兜底默认）、模式声明机制。
  - 触发词扩充：`设计稿 / UI稿 / UI设计稿 / UI图 / 设计图 / 视觉稿 / 高保真 / 视觉还原` 及英文 `design spec / visual design / high-fidelity / hi-fi / UI mockup / mockup` 等；并含「强制组件规范词」（优先级最高，如「用默认样式 / antd 默认」）。
- 新增「页面结构生成规则」：默认模式下结构由「内容清单 × Ant Design 页面模式规范」决定，不照搬原型图布局（上下/左右、单列、分组等均不采用）。
- 新增「查询区布局强制规则」（SKILL.md 第 12.3.1 节）：表格/列表上方查询区**一行最多展示 3 个筛选/输入框**，超 3 个自动换行、每行最多 3 个，查询/重置按钮紧随其后，用 `Form layout="inline"` 或 grid 组织。
- 模式一致性验证（Mode validation）：默认模式下检查产物是否残留图片的视觉与结构（非默认颜色/圆角/阴影、上下单列、筛选区每行超过 3 个等），有则恢复 Ant Design 默认结构样式。

### Fixed
- 修复参考文档硬编码「Ant Design 4.x」导致的版本逻辑不一致：`core/*.md`、`components/*.md` 中所有 `Ant Design 4.x` 改为按项目实际检测版本（版本检测见 SKILL.md 第 7 节；无项目默认最新稳定版）；官方文档链接由 `4x.ant.design` 统一为 `ant.design`。
- 修复「图片提供结构」残留表述：SKILL.md 第 1/5 节、`core/ant-design-rules.md` #2/#30 与最新「结构不照搬」逻辑统一。
- 修复 Modal 模板版本 API 歧义：`open` 标注为 Ant Design 5.x 属性，4.x 项目使用 `visible`。
- 修复 README 版本号与 `VERSION` 不一致（0.1.0 → 0.2.0）。

### Changed
- `SKILL.md`：新增第 2 节视觉模式；第 5/6/10/16/17/18/25/26/28/29 节补充模式前提；第 12 节结构生成规则；第 25 节 Mode validation；第 28 节执行算法并入模式判定。
- `core/ant-design-rules.md`：执行管线加入 Step 0 模式判定；#2/#3/#16/#19/#23/#24/#28/#30/#33 补充模式前提与查询区规则。
- `core/component-mapping.md`：核心原则与图片识别补充「结构/视觉不参与」模式前提。
- `core/page-patterns.md`：查询区「一行最多 3 个」规则与模式前提。
- `components/{button,input,select,table}.md`：Visual Design Mapping 澄清「外观仅用于语义识别，不用于视觉定制」；版本声明改为按项目实际版本。
- `README.md`：新增「Visual Mode」说明，决策流程图并入模式判定，版本号对齐；新增「Installation（安装方法）」「Usage（使用方法）」章节，便于团队快速安装与上手。

---

## [0.2.0]

### Added
- 基于 Ant Design 的组件识别与页面模式能力（List / Detail / Form / Dashboard 等）。
- 参考文档体系：`core/`（组件映射、页面模式、Ant Design 规则）与 `components/`（Button / Input / Select / Table）。
