# Peek-Free Login

[English](#english) | [简体中文](#简体中文)

## English

**Peek-Free Login** is a login-page demo built with **Vue 3 + TypeScript + Vite + GSAP + Ant Design Vue**.  
It features expressive animated characters on the left and a redesigned modern login panel on the right, including a privacy-friendly behavior where characters look away (top-left) when the password field is clicked/focused.

## Demo Video

- Local demo file: [`demo.mp4`]
- <video width="1666" height="839" alt="image" src="https://github.com/user-attachments/assets/a25e72f2-a48d-465f-98ae-3909719e4a0a" />
- GitHub usually supports inline preview for MP4. If it does not render in your page context, click the file link to view or download.


## Features

- Responsive two-column layout (desktop split, mobile single column)
- Animated character system on the left
  - pupils track mouse movement
  - random blinking behavior
  - characters react while typing username
  - characters react to password visibility state
  - privacy guard mode when password field is focused
- Login interaction logic on the right
  - required and length-based form validation
  - loading state on submit button
  - mock login request (frontend only)
  - stores token in `localStorage` and shows success message
- Fully customizable styles and component structure

## Style Notes

The right login panel has been significantly redesigned from the original style:

- glassmorphism card (transparency, border, shadow, blur)
- color system shifted from deep blue to teal gradients
- updated input radius, focus ring, and placeholder appearance
- stronger CTA button style with hover/press feedback
- rewritten title, subtitle, field labels, and helper copy
- removed help/privacy/footer links and third-party quick login

> The left animation area keeps the same core interaction logic and behavior continuity.

## Project Structure

```text
Peek-Free-Login/
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

## Run Locally

```bash
npm install
npm run dev
```

## Build

```bash
npm run build
```

## License

This project is fully open-source under the **MIT License**.  
See [`LICENSE`](./LICENSE) and [`COPYRIGHT.md`](./COPYRIGHT.md).

---

## 简体中文

**Peek-Free Login（捂眼登录）** 是一个基于 **Vue 3 + TypeScript + Vite + GSAP + Ant Design Vue** 的登录页示例项目。  
项目核心亮点是左侧角色联动动画，右侧为重新设计后的现代化登录面板，并包含“点击/聚焦密码框后角色统一看向左上”的防偷看效果。

## 演示视频

- 本地视频文件：[`demo.mp4`](./demo.mp4)
- GitHub 通常可直接预览 MP4；若当前页面未内嵌显示，请点击链接在线查看或下载。

## 功能概览

- 响应式双栏布局（桌面双栏、移动端单栏）
- 左侧多角色动画联动
  - 眼球跟随鼠标移动
  - 随机眨眼动画
  - 输入账号时角色联动变化
  - 密码显示/隐藏触发不同状态
  - 点击/聚焦密码框触发“防偷看”模式
- 右侧登录交互逻辑
  - 表单必填和长度校验
  - 登录按钮 Loading 状态
  - 模拟登录请求（仅前端逻辑）
  - 登录成功后写入 `localStorage` 并提示消息
- 样式与组件结构可自由二次开发

## 样式说明

右侧登录区：

- 玻璃拟态卡片（半透明、描边、阴影、背景模糊）
- 主色从深蓝体系切换为青绿色渐变体系
- 输入框圆角、聚焦阴影、占位符颜色重设计
- 主按钮改为高对比渐变并增加悬浮/按压反馈
- 标题、副标题、字段文案、辅助文案全部重写
- 去除了帮助中心、隐私政策和第三方一键登录等模块

> 左侧动画区核心行为逻辑保持一致，保证动画体验连续性。
