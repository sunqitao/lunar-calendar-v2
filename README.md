# 纯净万年历 APP v2.0 - uni-app-x 版本

> 下一代跨端应用引擎 - 原生性能

## 📱 项目简介

基于 **uni-app-x** 框架开发的万年历应用，采用苹果 iOS 设计风格，实现原生级性能体验。

### ✨ 特性

- 🚀 **原生性能** - uvue 渲染引擎，编译为 Kotlin/Swift
- 🎨 **苹果风格** - 遵循 Apple HIG 设计规范
- 🌓 **深色模式** - 完整适配浅色/深色双主题
- 📅 **农历转换** - 集成 lunar-javascript
- 📱 **跨端支持** - Android / iOS / HarmonyOS / Web / 小程序

## 🚀 快速开始

### 环境要求

- HBuilderX 4.0+
- uni-app-x 引擎

### 开发

```bash
# 使用 HBuilderX 打开项目
# 运行到手机或模拟器
```

### 构建

```bash
# 使用 HBuilderX 发行
# 选择 Android / iOS / 小程序等平台
```

## 📁 项目结构

```
lunar-calendar-v2-unix/
├── App.uvue          # 应用入口
├── main.js           # 主入口
├── manifest.json     # 应用配置
├── pages.json        # 页面配置
├── package.json      # 项目配置
└── pages/
    └── index/
        └── index.uvue  # 主页面
```

## 🎨 设计规范

### 配色系统

| 用途 | 浅色模式 | 深色模式 |
|------|----------|----------|
| 背景 | #FFFFFF | #000000 |
| 主背景 | #F2F2F7 | #1C1C1E |
| 主文字 | #000000 | #FFFFFF |
| 次要文字 | #8E8E93 | #8E8E93 |
| 强调色 | #007AFF | #0A84FF |

### 字体规范

| 用途 | 字号 | 字重 |
|------|------|------|
| 大标题 | 34px | Bold |
| 日期数字 | 28px | Regular |
| 农历 | 12px | Regular |

## 📱 平台支持

- ✅ Android (原生 Kotlin)
- ✅ iOS (原生 Swift)
- ✅ HarmonyOS (ArkTS)
- ✅ Web
- ✅ 微信小程序

## 📄 许可证

MIT License

---

**版本**: 2.0.0  
**框架**: uni-app-x  
**创建时间**: 2026-03-11
