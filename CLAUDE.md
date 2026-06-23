# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

计算机专业学生个人网站，使用 Vue 3 + Vite 构建的单页应用。

## Commands

```
npm run dev      # 启动开发服务器 (localhost:5173)
npm run build    # 生产构建，输出到 dist/
npm run preview  # 预览生产构建
```

## Architecture

单页应用，所有板块垂直排布在首页，导航点击平滑滚动到对应区域。

```
App.vue
├── NavBar.vue          # 固定顶部导航，IntersectionObserver 高亮当前板块
├── HeroSection.vue     # 全屏首屏，打字机效果循环展示角色标签
├── AboutSection.vue    # 两栏布局（头像+文字），教育经历时间线
├── SkillsSection.vue   # 技能分组卡片 + 进度条
├── ProjectsSection.vue # 项目卡片网格（占位图+描述+技术标签+链接）
├── ContactSection.vue  # 联系方式卡片（Email/GitHub/LinkedIn）
└── Footer.vue          # 版权信息
```

## Data & State

- **纯静态站点**：无路由、无 API 调用、无后端。所有内容数据（技能列表、项目卡片、联系方式等）都写在对应组件的 `<script setup>` 中，修改内容直接编辑对应数组或变量。
- **唯一的跨组件通信**：`App.vue` 通过 `provide('activeSection')` 向子孙组件注入当前可见板块标识，`NavBar.vue` 通过 `inject` 接收用于高亮导航项。
- **滚动高亮逻辑**：`NavBar.vue` 在 `onMounted` 中用 `IntersectionObserver`（threshold 0.3，rootMargin `-64px 0px -50% 0px`）检测各板块可见性，自动更新 `activeSection`。
- **CSS 与 NavBar 协调**：`html { scroll-padding-top: var(--nav-height) }` 确保平滑滚动时内容不被固定导航栏遮挡。

## Design System

- **配色**: 深色背景 `#0a0a1a`，渐变主色 `#6366f1 → #8b5cf6 → #06b6d4`，霓虹点缀 `#00f5ff`
- **特效**: 固定旋转渐变背景 (`.bg-gradient`)、网格覆盖层 (`.grid-overlay`)、玻璃拟态卡片 (`.glass-card`)、悬浮发光边框
- **响应式**: 768px 断点，NavBar 切换为汉堡菜单，网格布局切换为单列
- **CSS 自定义属性** 在 `src/styles/main.css` 的 `:root` 中定义，是整个站点的 design token 层。修改 `--accent-*`、`--bg-*`、`--text-*`、`--font-*` 等变量即可全局调整样式。

## Behavioral Guidelines

The parent directory `C:\Users\蔡广深\Desktop\CLAUDE.md` contains general coding guidelines that apply here. Key principles: think before coding, prefer simplicity, make surgical changes, and work toward verifiable goals.
