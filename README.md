# tdesign-skill

这是一个用于辅助前端开发（特别是基于 Vue 和 TDesign）的 AI 助手 Skill 指南。当你在项目中执行代码生成、样式修改等任务时，请严格遵守以下核心规则：

## 1. 样式与主题变量规范
- **强制使用 CSS 变量**：在编写或修改任何样式代码（CSS/LESS/SCSS）时，必须使用项目定义的主题变量，禁止直接硬编码颜色、尺寸等样式属性值。
- **变量文件定位与应用**：
  - 优先读取并使用以下变量文件中的变量：`node_modules/micro-common/styles/td-styles/tdesign-custom-theme.css`。
  - **如果该路径不存在**，你必须主动通过搜索工具在当前项目中全局查找 `tdesign-custom-theme.css` 文件，并读取该文件中的变量应用到后续的样式代码中。

## 2. Vue 与 TDesign 版本自动适配
在提供任何组件代码或建议之前，你必须先检查当前项目（通过读取 `package.json`）的依赖配置以确认技术栈版本：
- **分析 Vue 版本并适配 TDesign**：
  - 如果项目使用的是 **Vue 2**，你必须使用 `tdesign-vue` 组件库，并生成完全兼容 Vue 2 的代码。
  - 如果项目使用的是 **Vue 3**，你必须使用 `tdesign-vue-next` 组件库，并生成完全兼容 Vue 3（推荐 Composition API / `<script setup>`）的代码。

## 3. 结果验证机制
完成代码编写或修改后，**结果必须经过验证**。你需要在提交最终回复前执行以下验证步骤：
- **变量有效性验证**：核对你所引用的 CSS 变量是否真实存在于找到的 `tdesign-custom-theme.css` 文件中，避免使用不存在的变量。
- **API 准确性验证**：核对代码中的组件属性（Props）、事件（Events）和插槽（Slots）是否完全符合已确定的对应版本 TDesign（`tdesign-vue` 或 `tdesign-vue-next`）的官方文档规范。
- **运行/语法验证**：如果具备终端环境，请尝试运行项目的类型检查或 Lint 命令（例如 `npm run lint` / `vue-tsc --noEmit`），确保你修改的代码没有引发新的错误。
