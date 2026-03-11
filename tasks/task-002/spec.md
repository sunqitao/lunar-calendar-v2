# Task-002: UI 设计 - 苹果风格日历界面

## 🎯 任务目标
基于 Phase 1 的设计参考文档，完成纯净万年历 APP v2.0 的完整 UI 设计，输出设计稿和组件规范。

## 📋 工作内容

### 1. 日历主界面设计
- 月份视图（7 列网格布局）
- 日期卡片设计（圆角 10-12px）
- 今日标记（蓝色圆点 #007AFF）
- 农历日期显示（小字号，系统灰 #8E8E93）

### 2. 配色方案实现
- **浅色模式**：
  - 背景：白色 #FFFFFF
  - 主色：iOS 系统蓝 #007AFF
  - 文字：黑色 #000000 / 灰色 #8E8E93
- **深色模式**：
  - 背景：深灰 #1C1C1E
  - 主色：系统蓝 #0A84FF
  - 文字：白色 #FFFFFF / 灰色 #8E8E93

### 3. 字体规范应用
- 大标题：34pt Bold（SF Pro / 苹方）
- 标题：22pt Semibold
- 正文：17pt Regular
- 辅助信息：14pt / 12pt

### 4. 交互动效设计
- 月份切换动画（300-400ms ease-in-out）
- 日期选择反馈
- 滚动惯性效果
- 确保 60fps 流畅度

### 5. 组件库输出
- 日历网格组件
- 日期卡片组件
- 导航栏组件
- 详情面板组件

## 📤 交付物

1. **UI 设计稿** (`ui-design.fig` 或等效格式)
   - 浅色模式完整界面
   - 深色模式完整界面
   - 关键交互状态

2. **组件规范文档** (`component-spec.md`)
   - 各组件尺寸、间距、颜色
   - 动画参数（时长、缓动函数）
   - 响应式适配规则

3. **设计资源包** (`assets/`)
   - 图标资源
   - 颜色变量表
   - 字体样式表

## ⏱️ 预计时间
2 小时

## ✅ 完成标准
- [ ] UI 设计稿完成（浅色 + 深色）
- [ ] 组件规范文档完成
- [ ] 设计资源包整理完成
- [ ] 文档上传至任务目录
- [ ] 在项目中 @mention Frontend-Coder 交接

## 🔗 参考文档
- Phase 1 输出：`/root/hiclaw-fs/shared/tasks/lunar-task-001/design-reference.md`
- 功能优先级：`/root/hiclaw-fs/shared/tasks/lunar-task-001/feature-priority.md`
- Apple HIG: https://developer.apple.com/design/human-interface-guidelines/
