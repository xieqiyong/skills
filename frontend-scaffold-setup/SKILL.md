---
name: nuxt3-vue3-admin-scaffold
description: 基于 Nuxt 3、Vue 3、TypeScript 和 Nuxt UI 搭建前端脚手架，内置路由约定、请求封装、工具类组织、权限扩展思路，并提供主流富文本编辑器接入规范，适用于中后台、SaaS 控制台和企业级 Web 项目。
---

# Nuxt3 Vue3 Admin Scaffold

## 目标
这个 Skill 用于帮助用户快速生成一个基于 **Nuxt 3 + Vue 3 + TypeScript + Nuxt UI** 的前端脚手架，重点解决以下问题：

- 项目基础结构统一
- 路由组织规范
- 页面布局统一
- API 请求统一封装
- 工具类、hooks、常量、类型定义统一管理
- 支持中后台常见页面形态
- 提供主流富文本编辑器的集成建议与接入位置

输出结果应尽量做到：
- 可以直接初始化项目
- 可以直接复制核心代码
- 能作为团队项目模板继续扩展
- 不做过度设计，但保留扩展能力

---

## 适用场景

适合以下项目：

- 企业后台管理系统
- SaaS 控制台
- 内容管理系统（CMS）
- 带表单、列表、详情页的业务系统
- 需要富文本编辑能力的管理端项目
- 需要统一布局、统一请求层、统一工具层的前端项目

---

## 不适用场景

以下场景不作为本 Skill 的主要目标：

- 原生 App
- 小程序
- 非 Vue 技术栈项目
- 纯静态官网落地页
- 重度图形编辑器项目
- 已有成熟工程的深度重构

---

## 默认技术栈

当用户没有特别指定时，默认采用以下方案：

- Framework: **Nuxt 3**
- Language: **TypeScript**
- UI Framework: **Nuxt UI**
- Core View Layer: **Vue 3**
- Routing: **Nuxt Pages Router（文件路由） + route middleware**
- State: **Pinia**
- Request Layer: **基于 `$fetch` 二次封装**
- Styling:
    - Nuxt UI 默认能力
    - 必要时配合自定义 `assets/css/main.css`
- Form Validation:
    - 默认可结合 `zod`
- Rich Text Editors:
    - **Tiptap**
    - **WangEditor**
    - **Quill**
    - **TinyMCE**
    - 如用户有企业级复杂富文本需求，优先推荐 Tiptap 或 TinyMCE

---

## 触发条件

当用户有以下意图时，使用本 Skill：

- “帮我搭一个 Nuxt3 管理后台脚手架”
- “用 Vue3 + TS + Nuxt UI 生成一个项目模板”
- “帮我做一个带请求封装和工具类的 Nuxt 项目骨架”
- “搭一个企业级前端脚手架”
- “我想用 Nuxt 做后台系统，帮我出目录结构和基础代码”
- “要有路由、权限、utils、编辑器方案的前端模板”

---

## 核心能力

这个 Skill 应该能够输出以下内容：

1. 项目初始化命令
2. 推荐目录结构
3. Nuxt 核心配置
4. 全局布局与应用壳
5. 页面路由组织方式
6. 登录鉴权中间件示例
7. 请求层封装
8. 工具类目录与典型方法
9. composables 组织方式
10. Pinia store 基础结构
11. 富文本编辑器接入位置与封装建议
12. 常用业务页面示例：
- 登录页
- 仪表盘
- 列表页
- 详情页
- 富文本编辑页

---

## 默认输出策略

当用户没有进一步限制时，默认输出应满足：

- 使用 **Nuxt 3 官方约定式目录**
- 保持中后台项目常见分层
- 优先生成最小可运行版本
- 代码偏实用，不堆过多概念
- 路由和请求层具备后续扩展能力
- 富文本编辑器采用“按需接入、统一封装”的方式

---

## 工作流程

### 第一步：识别项目类型
优先判断用户项目属于哪类：

- 通用后台
- 内容管理系统
- SaaS 控制台
- 需要富文本能力的运营后台
- 多模块业务管理系统

如果用户没有明确说明，默认按 **通用企业级管理后台** 处理。

### 第二步：确定默认架构
默认使用：

- Nuxt 3
- Vue 3
- TypeScript
- Nuxt UI
- Pinia
- route middleware
- composables + utils + services 分层
- `$fetch` 请求封装

### 第三步：生成脚手架结构
输出内容应尽量包含：

- 安装命令
- 目录结构
- 关键配置文件
- 布局文件
- 页面示例
- 中间件示例
- 请求封装示例
- 富文本编辑器接入建议

### 第四步：保证可扩展
输出的项目骨架要支持继续扩展：

- 权限系统
- 多环境配置
- 多编辑器切换
- 上传组件
- 表单校验
- 列表搜索筛选
- 国际化

---

## 推荐目录结构

```txt
.
├─ app.vue
├─ nuxt.config.ts
├─ assets/
│  └─ css/
│     └─ main.css
├─ components/
│  ├─ base/
│  │  ├─ BaseTable.vue
│  │  ├─ BaseSearchForm.vue
│  │  ├─ BasePageHeader.vue
│  │  └─ BaseStatusTag.vue
│  ├─ layout/
│  │  ├─ AppSidebar.vue
│  │  ├─ AppHeader.vue
│  │  ├─ AppBreadcrumb.vue
│  │  └─ AppContainer.vue
│  ├─ business/
│  │  ├─ UserSelect.vue
│  │  └─ UploadImage.vue
│  └─ editor/
│     ├─ TiptapEditor.vue
│     ├─ WangEditor.vue
│     ├─ QuillEditor.vue
│     └─ TinyMceEditor.vue
├─ composables/
│  ├─ useAuth.ts
│  ├─ usePagination.ts
│  ├─ usePermission.ts
│  ├─ useRequest.ts
│  └─ useEditor.ts
├─ layouts/
│  ├─ default.vue
│  ├─ blank.vue
│  └─ admin.vue
├─ middleware/
│  ├─ auth.ts
│  ├─ guest.ts
│  └─ permission.ts
├─ pages/
│  ├─ index.vue
│  ├─ login.vue
│  ├─ dashboard/
│  │  └─ index.vue
│  ├─ system/
│  │  ├─ user/
│  │  │  ├─ index.vue
│  │  │  └─ [id].vue
│  │  └─ role/
│  │     └─ index.vue
│  └─ content/
│     ├─ article/
│     │  ├─ index.vue
│     │  ├─ create.vue
│     │  └─ edit/[id].vue
│     └─ editor-demo.vue
├─ plugins/
│  ├─ api.ts
│  ├─ dayjs.ts
│  └─ editor.client.ts
├─ server/
│  └─ api/
│     └─ health.get.ts
├─ stores/
│  ├─ app.ts
│  ├─ auth.ts
│  └─ permission.ts
├─ types/
│  ├─ api.ts
│  ├─ auth.ts
│  ├─ user.ts
│  └─ editor.ts
├─ utils/
│  ├─ auth.ts
│  ├─ storage.ts
│  ├─ request.ts
│  ├─ download.ts
│  ├─ format.ts
│  ├─ tree.ts
│  ├─ validate.ts
│  ├─ editor.ts
│  └─ constants.ts
└─ services/
   ├─ auth.ts
   ├─ user.ts
   ├─ role.ts
   └─ content.ts