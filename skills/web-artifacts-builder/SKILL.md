---
name: web-artifacts-builder
description: 用于使用现代前端网络技术（React、Tailwind CSS、shadcn/ui）创建复杂、多组件的 claude.ai HTML 工件的工具套件。用于需要状态管理、路由或 shadcn/ui 组件的复杂工件 - 不适用于简单的单文件 HTML/JSX 工件。
license: 完整条款见 LICENSE.txt
---

# Web Artifacts Builder

要构建强大的前端 claude.ai 工件，请按照以下步骤操作：
1. 使用 `scripts/init-artifact.sh` 初始化前端仓库
2. 通过编辑生成的代码来开发您的工件
3. 使用 `scripts/bundle-artifact.sh` 将所有代码捆绑到单个 HTML 文件中
4. 向用户显示工件
5. （可选）测试工件

**技术栈**：React 18 + TypeScript + Vite + Parcel（捆绑）+ Tailwind CSS + shadcn/ui

## 设计和样式指南

非常重要：为避免通常被称为"AI 劣质设计"的问题，请避免使用过多的居中布局、紫色渐变、统一的圆角和 Inter 字体。

## 快速开始

### 步骤 1：初始化项目

运行初始化脚本来创建一个新的 React 项目：
```bash
bash scripts/init-artifact.sh <project-name>
cd <project-name>
```

这会创建一个完全配置好的项目，包含：
- ✅ React + TypeScript（通过 Vite）
- ✅ Tailwind CSS 3.4.1 与 shadcn/ui 主题系统
- ✅ 配置好的路径别名 (`@/`)
- ✅ 40+ 个预安装的 shadcn/ui 组件
- ✅ 包含所有 Radix UI 依赖项
- ✅ 配置好的 Parcel（通过 .parcelrc）用于捆绑
- ✅ Node 18+ 兼容性（自动检测并固定 Vite 版本）

### 步骤 2：开发您的工件

要构建工件，请编辑生成的文件。请参阅下面的**常见开发任务**以获取指导。

### 步骤 3：捆绑到单个 HTML 文件

要将 React 应用捆绑到单个 HTML 工件中：
```bash
bash scripts/bundle-artifact.sh
```

这会创建 `bundle.html` - 一个自包含的工件，其中内联了所有 JavaScript、CSS 和依赖项。此文件可以作为工件直接在 Claude 对话中共享。

**要求**：您的项目根目录中必须有一个 `index.html` 文件。

**脚本功能**：
- 安装捆绑依赖项（parcel、@parcel/config-default、parcel-resolver-tspaths、html-inline）
- 创建带有路径别名支持的 `.parcelrc` 配置
- 使用 Parcel 构建（无源代码映射）
- 使用 html-inline 将所有资产内联到单个 HTML 中

### 步骤 4：与用户共享工件

最后，在与用户的对话中共享捆绑的 HTML 文件，以便他们可以将其视为工件。

### 步骤 5：测试/可视化工件（可选）

注意：这是一个完全可选的步骤。仅在必要或请求时执行。

要测试/可视化工件，请使用可用的工具（包括其他技能或内置工具，如 Playwright 或 Puppeteer）。一般来说，避免预先测试工件，因为这会增加请求与成品工件可见之间的延迟。如果有请求或出现问题，请在呈现工件后再进行测试。

## 参考

- **shadcn/ui 组件**：https://ui.shadcn.com/docs/components