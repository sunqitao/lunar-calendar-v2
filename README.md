# 纯净万年历 APP v2.0

> 苹果风格设计的农历日历应用

## 📱 项目简介

纯净万年历 v2.0 采用 **Apple Human Interface Guidelines** 设计规范，打造简洁、现代、优雅的日历体验。

### ✨ 特性

- 🎨 **苹果风格 UI** - 遵循 iOS 设计语言，简洁优雅
- 🌓 **深色模式** - 完整适配浅色/深色双主题
- 📅 **农历转换** - 集成 lunar-javascript，准确计算农历、生肖、干支、宜忌
- 🎯 **今日标记** - 蓝色圆点优雅标记今日
- 🔄 **流畅动画** - 60fps 月份切换动画
- 📱 **响应式** - 适配手机、平板、桌面设备
- ♿ **无障碍** - 支持 ARIA 标签和动态字体

## 🚀 快速开始

### 安装依赖

```bash
cd /root/hiclaw-fs/shared/projects/lunar-calendar-v2
npm install
```

### 开发模式

```bash
npm run dev
```

### 构建生产版本

```bash
npm run build
```

## 📁 项目结构

```
lunar-calendar-v2/
├── index.html          # HTML 入口
├── package.json        # 项目配置
├── vite.config.js      # Vite 配置
├── public/
│   └── favicon.svg     # 应用图标
└── src/
    ├── main.js         # 应用入口
    ├── App.vue         # 主应用组件
    └── styles.css      # 全局样式（含主题系统）
```

## 🎨 设计规范

### 配色系统

#### 浅色模式
| 用途 | 色值 |
|------|------|
| 背景色 | `#FFFFFF` |
| 主背景 | `#F2F2F7` |
| 主文字 | `#000000` |
| 次要文字 | `#8E8E93` |
| 强调色 | `#007AFF` |

#### 深色模式
| 用途 | 色值 |
|------|------|
| 背景色 | `#000000` |
| 主背景 | `#1C1C1E` |
| 主文字 | `#FFFFFF` |
| 次要文字 | `#8E8E93` |
| 强调色 | `#0A84FF` |

### 字体规范

| 用途 | 字号 | 字重 |
|------|------|------|
| 大标题 | 34pt | Bold |
| 日期数字 | 28pt | Regular |
| 正文 | 17pt | Regular |
| 农历 | 12pt | Regular |

### 动画规范

| 场景 | 时长 | 缓动 |
|------|------|------|
| 月份切换 | 400ms | ease-in-out |
| 按钮点击 | 150ms | ease-out |
| 主题切换 | 300ms | ease-in-out |

## 🔧 技术栈

- **框架**: Vue 3.4 + Composition API
- **构建**: Vite 5
- **农历库**: lunar-javascript 1.6
- **样式**: CSS 变量 + Scoped CSS

## 📋 功能清单

### P0 核心功能 ✅
- [x] 日历网格布局
- [x] 农历转换引擎
- [x] 浅色模式 UI
- [x] 今日标记

### P1 交互优化 ✅
- [x] 月份切换动画
- [x] 深色模式适配
- [x] 节假日标记
- [x] 点击反馈

### P2 增强功能 ✅
- [x] 详情面板（宜忌/生肖/干支）
- [x] 日期选择交互
- [x] 主题切换按钮

## 🎯 使用说明

### 基本操作
- **左右箭头**: 切换上/下月份
- **点击日期**: 查看日期详情（农历、宜忌等）
- **主题按钮**: 切换浅色/深色模式

### 主题切换
- 支持手动切换主题
- 支持跟随系统自动切换
- 用户选择持久化保存

## 📱 浏览器支持

- iOS Safari 14+
- Android Chrome 90+
- Desktop Chrome/Safari/Firefox/Edge

## 📄 许可证

MIT License

---

**版本**: 2.0.0  
**创建时间**: 2026-03-11  
**开发者**: Frontend-Coder
