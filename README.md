# Peek-Free Login

**Peek-Free Login（捂眼登录）** 是一个基于 **Vue 3 + TypeScript + Vite + GSAP + Ant Design Vue** 的登录页示例项目。  
项目核心亮点是左侧角色联动动画，右侧为重新设计后的现代化登录面板，并包含“点击密码框后角色避嫌看向左上”的防偷看效果。

## 功能概览

- 响应式双栏布局（桌面双栏、移动端单栏）
- 左侧多角色动画联动
  - 眼球跟随鼠标移动
  - 随机眨眼动画
  - 输入账号时角色互相对视
  - 输入密码时角色状态变化
  - 切换密码可见时触发“观察密码”动作
- 右侧登录交互逻辑
  - 表单必填和长度校验
  - 登录按钮 Loading 状态
  - 模拟登录请求（本地 mock）
  - 登录成功后写入 `localStorage` 并提示消息
- 全局样式与组件样式均可直接二次开发

## 样式设计说明

右侧登录区已做明显差异化改造（相较原始版本）：

- 使用玻璃拟态卡片（半透明、描边、阴影、模糊背景）
- 主色从深蓝体系切换为青绿渐变体系
- 输入框圆角、聚焦阴影、占位符颜色重新设计
- 主按钮改为高对比渐变按钮并加入悬浮/按压反馈
- 标题、副标题、字段命名和底部提示文案均已重写
- 去除了帮助中心、隐私政策、第三方一键登录等无关区块

> 说明：左侧动画区的核心逻辑与行为保持一致，确保动画体验完整保留。

## 目录结构

```text
vue/
  src/
    components/
      AnimatedCharacters.vue
      FeishuIcon.ts
    pages/
      Login/
        index.vue
        index.css
    App.vue
    main.ts
```

## 本地运行

```bash
npm install
npm run dev
```

## 构建产物

```bash
npm run build
```

## 开源与版权

本项目采用 **MIT License** 开源发布，可自由使用、修改、分发、商用。  
详细条款见 [`LICENSE`](./LICENSE) 与 [`COPYRIGHT.md`](./COPYRIGHT.md)。
