# Task-003: 前端实现 - 苹果风格日历

## 🎯 任务目标
基于 Phase 2 的 UI 设计规范，实现纯净万年历 APP v2.0 的前端代码，打造流畅的苹果风格日历体验。

## 📋 工作内容

### P0 核心功能（2 小时）
1. **项目框架搭建**
   - Vue 3 + Composition API
   - uni-app 跨端框架配置
   - 项目目录结构

2. **农历转换引擎集成**
   - 集成 `lunar-javascript` 库
   - 实现公历→农历转换
   - 生肖、干支计算

3. **日历网格组件**
   - 7 列网格布局（CSS Grid）
   - 日期卡片渲染
   - 月份切换逻辑

4. **浅色模式 UI**
   - iOS 系统蓝 #007AFF
   - 系统灰 #8E8E93
   - 苹方/SF Pro 字体

### P1 交互优化（1 小时）
5. **今日标记**
   - 蓝色圆点标识
   - 简洁优雅风格

6. **月份切换动画**
   - 300-400ms ease-in-out
   - 60fps 流畅度（transform + will-change）
   - 滑动切换手势

7. **深色模式适配**
   - CSS 变量主题管理
   - 跟随系统切换

8. **节假日标记**
   - 法定节假日标识
   - 调休标识

### P2 增强功能（1 小时）
9. **详情面板**
   - 宜忌展示
   - 生肖、干支详情
   - 农历详细信息

10. **日期选择器**
    - 年份/月份选择
    - 快速跳转

11. **测试优化**
    - 功能测试
    - 性能优化
    - Bug 修复

## 📤 交付物

1. **源代码** (`src/`)
   - Vue 3 组件
   - 样式文件（含深色模式）
   - 工具函数（农历转换）

2. **构建输出** (`dist/`)
   - 可运行的 H5 应用
   - 小程序包（可选）

3. **开发文档** (`README.md`)
   - 项目结构说明
   - 开发环境配置
   - 构建命令

## ⏱️ 预计时间
3 小时

## ✅ 完成标准
- [ ] 日历主界面完成（浅色 + 深色）
- [ ] 农历转换功能正常
- [ ] 月份切换动画流畅（60fps）
- [ ] 今日标记正确显示
- [ ] 节假日标记完成
- [ ] 详情面板完成
- [ ] 代码提交到 main 分支
- [ ] 在项目中 @mention Manager 和 PM 汇报

## 🔗 参考文档
- UI 设计规范：`/root/hiclaw-fs/shared/projects/lunar-calendar-v2/tasks/task-002/design/ui-spec-calendar.md`
- Phase 1 设计参考：`/root/hiclaw-fs/shared/tasks/lunar-task-001/design-reference.md`
- 功能优先级：`/root/hiclaw-fs/shared/tasks/lunar-task-001/feature-priority.md`
- lunar-javascript: https://github.com/6tail/lunar-javascript

## 🔧 技术规范
- **提交分支**: `main`（直接提交）
- **提交格式**: `feat:`, `style:`, `perf:`, `fix:`
- **Git 用户**: `frontend-coder@hiclaw.local`
