# 纯净万年历 APP v2.0 - UI 设计规范

**版本**: 1.0  
**创建时间**: 2026-03-11  
**设计师**: UI-Designer  
**风格**: 苹果 iOS 风格

---

## 一、设计原则

遵循 **Apple Human Interface Guidelines**，打造简洁、现代、优雅的日历应用。

### 核心原则
1. **简洁清晰** - 去除冗余元素，突出核心信息
2. **层次分明** - 通过字体大小、颜色、阴影建立视觉层次
3. **流畅自然** - 60fps 动画，300-400ms 过渡时间
4. **一致统一** - 全应用使用统一的设计语言

---

## 二、色彩系统

### 2.1 浅色模式 (Light Mode)

| 用途 | 色值 | 说明 |
|------|------|------|
| 背景色 | `#FFFFFF` | 纯白背景 |
| 主背景 | `#F2F2F7` | iOS 系统灰背景（分组背景） |
| 主文字 | `#000000` | 主要信息（日期数字） |
| 次要文字 | `#8E8E93` | iOS 系统灰（农历、辅助信息） |
| 强调色 | `#007AFF` | iOS 系统蓝（今日标记、选中状态） |
| 分隔线 | `#C6C6C8` | 卡片分隔 |
| 危险色 | `#FF3B30` | 删除、警告 |
| 成功色 | `#34C759` | 完成、成功状态 |

### 2.2 深色模式 (Dark Mode)

| 用途 | 色值 | 说明 |
|------|------|------|
| 背景色 | `#000000` | 纯黑背景 |
| 主背景 | `#1C1C1E` | iOS 系统深灰（卡片背景） |
| 主文字 | `#FFFFFF` | 主要信息 |
| 次要文字 | `#8E8E93` | 辅助信息 |
| 强调色 | `#0A84FF` | iOS 系统蓝（深色模式变体） |
| 分隔线 | `#38383A` | 卡片分隔 |
| 危险色 | `#FF453A` | 删除、警告 |
| 成功色 | `#30D158` | 完成、成功状态 |

### 2.3 CSS 变量定义

```css
/* 浅色模式 */
:root[data-theme="light"] {
  --bg-primary: #FFFFFF;
  --bg-secondary: #F2F2F7;
  --text-primary: #000000;
  --text-secondary: #8E8E93;
  --accent: #007AFF;
  --separator: #C6C6C8;
  --danger: #FF3B30;
  --success: #34C759;
}

/* 深色模式 */
:root[data-theme="dark"] {
  --bg-primary: #000000;
  --bg-secondary: #1C1C1E;
  --text-primary: #FFFFFF;
  --text-secondary: #8E8E93;
  --accent: #0A84FF;
  --separator: #38383A;
  --danger: #FF453A;
  --success: #30D158;
}
```

---

## 三、字体规范

### 3.1 字体家族

```css
:root {
  /* 中文优先苹方，英文优先 SF Pro */
  --font-family: "PingFang SC", "SF Pro SC", "SF Pro Text", 
                 "Helvetica Neue", Helvetica, Arial, sans-serif;
}
```

### 3.2 字号层级

| 用途 | 字号 | 字重 | 行高 | 说明 |
|------|------|------|------|------|
| 大标题 | 34pt (45px) | Bold (700) | 1.1 | 月份标题（如"2026 年 3 月"） |
| 标题 | 22pt (29px) | Semibold (600) | 1.2 | 页面标题 |
| 副标题 | 17pt (23px) | Regular (400) | 1.3 | 副标题信息 |
| 正文 | 17pt (23px) | Regular (400) | 1.4 | 主要内容 |
| 日期数字 | 28pt (37px) | Regular (400) | 1.0 | 日历日期 |
| 今日数字 | 28pt (37px) | Medium (500) | 1.0 | 今日日期（加粗） |
| 农历 | 12pt (16px) | Regular (400) | 1.4 | 农历日期 |
| 宜忌 | 11pt (15px) | Regular (400) | 1.4 | 宜忌文字 |
| 辅助文字 | 13pt (17px) | Regular (400) | 1.3 | 说明文字 |
| 按钮文字 | 17pt (23px) | Semibold (600) | 1.2 | 按钮文字 |

### 3.3 字体颜色应用

```css
/* 主要文字 - 高对比度 */
.text-primary {
  color: var(--text-primary);
  opacity: 1;
}

/* 次要文字 - 中等对比度 */
.text-secondary {
  color: var(--text-secondary);
}

/* 禁用文字 - 低对比度 */
.text-disabled {
  color: var(--text-secondary);
  opacity: 0.5;
}
```

---

## 四、布局规范

### 4.1 间距系统

基于 8px 网格系统：

```css
:root {
  --spacing-xs: 4px;
  --spacing-sm: 8px;
  --spacing-md: 16px;
  --spacing-lg: 24px;
  --spacing-xl: 32px;
  --spacing-xxl: 48px;
}
```

### 4.2 圆角规范

| 元素 | 圆角 | 说明 |
|------|------|------|
| 日期卡片 | 10px | 统一圆角 |
| 按钮 | 10px | 标准按钮 |
| 输入框 | 10px | 表单输入 |
| 卡片容器 | 12px | 内容卡片 |
| 弹窗 | 14px | 模态弹窗 |
| 今日标记圆点 | 50% | 圆形 |

```css
:root {
  --radius-sm: 8px;
  --radius-md: 10px;
  --radius-lg: 12px;
  --radius-xl: 14px;
  --radius-round: 50%;
}
```

### 4.3 阴影规范

```css
/* 轻微阴影 - 卡片层级 */
.shadow-sm {
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1),
              0 1px 2px rgba(0, 0, 0, 0.06);
}

/* 中等阴影 - 悬浮状态 */
.shadow-md {
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1),
              0 2px 4px rgba(0, 0, 0, 0.06);
}

/* 强调阴影 - 弹窗 */
.shadow-lg {
  box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1),
              0 4px 6px rgba(0, 0, 0, 0.05);
}

/* 深色模式阴影（更柔和） */
[data-theme="dark"] .shadow-sm {
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.3),
              0 1px 2px rgba(0, 0, 0, 0.2);
}
```

---

## 五、组件库

### 5.1 日历主界面

#### 布局结构
```
┌─────────────────────────────────┐
│  ←  2026 年 3 月        年 →    │  顶部导航栏
├─────────────────────────────────┤
│  日   一   二   三   四   五   六 │  星期标题
├─────────────────────────────────┤
│      [1]  [2]  [3]  [4]  [5]   │
│  [6]  [7]  [8]  [9] [10] [11]  │
│ [12] [13] [●] [15] [16] [17]  │  日期网格
│ [18] [19] [20] [21] [22] [23]  │  （今日蓝色圆点）
│ [24] [25] [26] [27] [28] [29]  │
│ [30] [31]                      │
├─────────────────────────────────┤
│  农历：二月十三                │  农历信息
│  宜：祭祀 祈福  忌：动土 安葬   │  宜忌信息
└─────────────────────────────────┘
```

#### 日期卡片样式
```css
.date-cell {
  width: 14.28%; /* 7 列均分 */
  aspect-ratio: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  border-radius: var(--radius-md);
  background: var(--bg-primary);
  transition: background-color 0.2s ease;
}

.date-cell:hover {
  background: var(--bg-secondary);
}

.date-cell.today {
  position: relative;
}

.date-cell.today::after {
  content: '';
  position: absolute;
  bottom: 8px;
  width: 6px;
  height: 6px;
  background: var(--accent);
  border-radius: 50%;
}

.date-cell.selected {
  background: var(--accent);
}

.date-cell.selected .date-number {
  color: #FFFFFF;
}

.date-number {
  font-size: 23px;
  font-weight: 400;
  color: var(--text-primary);
}

.date-lunar {
  font-size: 11px;
  color: var(--text-secondary);
  margin-top: 2px;
}
```

### 5.2 月份选择器

#### 设计要点
- 滑动切换月份（支持手势）
- 顶部显示当前年月
- 左右箭头导航
- 点击年月弹出年份选择器

```css
.month-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: var(--spacing-md);
  background: var(--bg-primary);
  border-bottom: 1px solid var(--separator);
}

.month-title {
  font-size: 34pt;
  font-weight: 700;
  color: var(--text-primary);
}

.nav-button {
  width: 40px;
  height: 40px;
  border-radius: var(--radius-md);
  background: var(--bg-secondary);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

.nav-button:hover {
  background: var(--separator);
}

.nav-button:active {
  transform: scale(0.95);
}
```

### 5.3 今日标记

苹果风格今日标记采用**蓝色圆点**设计：

```css
.today-indicator {
  position: relative;
}

.today-indicator::after {
  content: '';
  position: absolute;
  bottom: 6px;
  left: 50%;
  transform: translateX(-50%);
  width: 6px;
  height: 6px;
  background: var(--accent);
  border-radius: 50%;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0%, 100% {
    opacity: 1;
    transform: translateX(-50%) scale(1);
  }
  50% {
    opacity: 0.7;
    transform: translateX(-50%) scale(1.1);
  }
}
```

### 5.4 农历信息卡片

```css
.lunar-card {
  background: var(--bg-secondary);
  border-radius: var(--radius-lg);
  padding: var(--spacing-lg);
  margin: var(--spacing-md);
}

.lunar-date {
  font-size: 17pt;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: var(--spacing-sm);
}

.lunar-info {
  font-size: 13pt;
  color: var(--text-secondary);
  line-height: 1.5;
}

.lunar-info strong {
  color: var(--text-primary);
  margin-right: var(--spacing-sm);
}
```

### 5.5 按钮组件

```css
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 12px 24px;
  border-radius: var(--radius-md);
  font-size: 17pt;
  font-weight: 600;
  border: none;
  cursor: pointer;
  transition: all 0.2s ease;
}

.btn-primary {
  background: var(--accent);
  color: #FFFFFF;
}

.btn-primary:hover {
  opacity: 0.9;
}

.btn-primary:active {
  transform: scale(0.98);
}

.btn-secondary {
  background: var(--bg-secondary);
  color: var(--text-primary);
}

.btn-secondary:hover {
  background: var(--separator);
}
```

---

## 六、交互动效规范

### 6.1 动画时长

| 场景 | 时长 | 缓动函数 |
|------|------|----------|
| 页面切换 | 400ms | ease-in-out |
| 月份滑动 | 300ms | ease-out |
| 按钮点击 | 150ms | ease-out |
| 卡片展开 | 300ms | cubic-bezier(0.4, 0, 0.2, 1) |
| 淡入淡出 | 250ms | ease-in-out |

### 6.2 月份切换动画

```css
.month-transition {
  transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1),
              opacity 0.25s ease-in-out;
}

.month-enter {
  transform: translateX(100%);
  opacity: 0;
}

.month-enter-active {
  transform: translateX(0);
  opacity: 1;
}

.month-exit {
  transform: translateX(0);
  opacity: 1;
}

.month-exit-active {
  transform: translateX(-100%);
  opacity: 0;
}
```

### 6.3 点击反馈

```css
.clickable {
  transition: transform 0.15s ease-out,
              background-color 0.2s ease;
}

.clickable:active {
  transform: scale(0.96);
  background-color: var(--separator);
}
```

### 6.4 滑动切换手势

- 支持左右滑动切换月份
- 滑动距离 > 50px 触发切换
- 跟随手指的实时位移
- 弹性边界效果

```css
.swipe-container {
  overflow: hidden;
  touch-action: pan-y pinch-zoom;
}

.swipe-content {
  display: flex;
  transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}
```

---

## 七、深色模式适配

### 7.1 主题切换逻辑

```javascript
// 主题管理
const themeManager = {
  setTheme(theme) {
    document.documentElement.setAttribute('data-theme', theme);
    localStorage.setItem('theme', theme);
  },
  
  getTheme() {
    return localStorage.getItem('theme') || 
           (window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light');
  },
  
  init() {
    this.setTheme(this.getTheme());
    
    // 监听系统主题变化
    window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', (e) => {
      if (!localStorage.getItem('theme')) {
        this.setTheme(e.matches ? 'dark' : 'light');
      }
    });
  }
};
```

### 7.2 深色模式特殊处理

1. **图片/图标**: 使用 SF Symbols 或自定义深色版本
2. **阴影**: 深色模式下使用更深的阴影颜色
3. **对比度**: 确保文字对比度符合 WCAG AA 标准（≥ 4.5:1）
4. **纯黑避免**: 卡片背景使用 `#1C1C1E` 而非纯黑

---

## 八、响应式适配

### 8.1 断点定义

```css
/* 手机竖屏 */
@media (max-width: 414px) {
  :root {
    --date-cell-size: 12vw;
  }
}

/* 手机横屏/小平板 */
@media (min-width: 415px) and (max-width: 768px) {
  :root {
    --date-cell-size: 10vw;
  }
}

/* 平板/桌面 */
@media (min-width: 769px) {
  .calendar-container {
    max-width: 500px;
    margin: 0 auto;
  }
}
```

### 8.2 安全区域适配

```css
/* iOS 安全区域 */
.safe-area {
  padding-top: env(safe-area-inset-top);
  padding-bottom: env(safe-area-inset-bottom);
  padding-left: env(safe-area-inset-left);
  padding-right: env(safe-area-inset-right);
}
```

---

## 九、可访问性

### 9.1 无障碍要求

- 所有交互元素添加 `aria-label`
- 日期数字使用 `<time>` 标签
- 颜色不单独作为信息载体
- 支持系统字体大小缩放

```html
<button 
  class="date-cell"
  aria-label="2026 年 3 月 14 日，农历二月十三"
  aria-current="date"
>
  <span class="date-number">14</span>
  <span class="date-lunar">廿三</span>
</button>
```

### 9.2 动态字体支持

```css
/* 支持系统字体大小设置 */
:root {
  font-size: calc(16px + 0.5vw);
}

/* 最小字号限制 */
.date-number {
  font-size: clamp(20px, 5vw, 37px);
}
```

---

## 十、交付清单

- [x] 色彩系统定义（浅色/深色）
- [x] 字体规范（字号、字重、行高）
- [x] 布局规范（间距、圆角、阴影）
- [x] 组件库（日历、按钮、卡片）
- [x] 交互动效规范
- [x] 深色模式适配方案
- [x] 响应式适配方案
- [x] 可访问性规范

---

## 附录：设计资源

### 推荐工具
- **设计**: Figma / Sketch
- **图标**: SF Symbols (iOS 官方图标库)
- **字体**: Apple 官网下载 SF Pro

### 参考文档
- [Apple Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/)
- [iOS Design Checklist](https://iosdesignchecklist.com/)

---

**文档结束**
