<template>
  <div id="app" :data-theme="theme">
    <div class="app-container safe-area">
      <!-- 主题切换按钮 -->
      <button class="theme-toggle" @click="toggleTheme" aria-label="切换主题">
        <svg v-if="theme === 'light'" viewBox="0 0 24 24">
          <path d="M12 3a9 9 0 109 9c0-.46-.04-.92-.1-1.36a5.389 5.389 0 01-4.4 2.26 5.403 5.403 0 01-3.14-9.8c-.44-.06-.9-.1-1.36-.1z"/>
        </svg>
        <svg v-else viewBox="0 0 24 24">
          <path d="M12 7c-2.76 0-5 2.24-5 5s2.24 5 5 5 5-2.24 5-5-2.24-5-5-5zM2 13h2c.55 0 1-.45 1-1s-.45-1-1-1H2c-.55 0-1 .45-1 1s.45 1 1 1zm18 0h2c.55 0 1-.45 1-1s-.45-1-1-1h-2c-.55 0-1 .45-1 1s.45 1 1 1zM11 2v2c0 .55.45 1 1 1s1-.45 1-1V2c0-.55-.45-1-1-1s-1 .45-1 1zm0 18v2c0 .55.45 1 1 1s1-.45 1-1v-2c0-.55-.45-1-1-1s-1 .45-1 1zM5.99 4.58a.996.996 0 00-1.41 0 .996.996 0 000 1.41l1.06 1.06c.39.39 1.03.39 1.41 0s.39-1.03 0-1.41L5.99 4.58zm12.37 12.37a.996.996 0 00-1.41 0 .996.996 0 000 1.41l1.06 1.06c.39.39 1.03.39 1.41 0a.996.996 0 000-1.41l-1.06-1.06zm1.06-10.96a.996.996 0 000-1.41.996.996 0 00-1.41 0l-1.06 1.06c-.39.39-.39 1.03 0 1.41s1.03.39 1.41 0l1.06-1.06zM7.05 18.36a.996.996 0 000-1.41.996.996 0 00-1.41 0l-1.06 1.06c-.39.39-.39 1.03 0 1.41s1.03.39 1.41 0l1.06-1.06z"/>
        </svg>
      </button>

      <!-- 月份导航栏 -->
      <header class="month-header">
        <button class="nav-button" @click="prevMonth" aria-label="上个月">
          <svg viewBox="0 0 24 24"><path d="M15.41 7.41L14 6l-6 6 6 6 1.41-1.41L10.83 12z"/></svg>
        </button>
        <h1 class="month-title">{{ currentYear }}年{{ currentMonth }}月</h1>
        <button class="nav-button" @click="nextMonth" aria-label="下个月">
          <svg viewBox="0 0 24 24"><path d="M10 6L8.59 7.41 13.17 12l-4.58 4.59L10 18l6-6z"/></svg>
        </button>
      </header>

      <!-- 星期标题 -->
      <div class="weekday-header">
        <div class="weekday-cell weekend" v-for="day in weekdays" :key="day" :class="{ weekend: day === '日' || day === '六' }">
          {{ day }}
        </div>
      </div>

      <!-- 日历网格 -->
      <div class="calendar-grid">
        <div
          v-for="cell in calendarDays"
          :key="cell.date.toISOString()"
          class="date-cell"
          :class="{
            'other-month': !cell.isCurrentMonth,
            'today': cell.isToday,
            'selected': cell.isSelected,
            'holiday': cell.isHoliday
          }"
          @click="selectDate(cell)"
          :aria-label="getAriaLabel(cell)"
          :aria-current="cell.isToday ? 'date' : undefined"
        >
          <span class="date-number">{{ cell.day }}</span>
          <span class="date-lunar">{{ cell.lunarDay }}</span>
        </div>
      </div>

      <!-- 农历信息卡片 -->
      <div class="lunar-card">
        <div class="lunar-date">{{ selectedLunar.toString() }}</div>
        <div class="lunar-info">
          <div>生肖：<strong>{{ selectedLunar.getYearShengXiao() }}</strong></div>
          <div>干支：<strong>{{ selectedLunar.getYearInGanZhi() }}年 {{ selectedLunar.getMonthInGanZhi() }}月 {{ selectedLunar.getDayInGanZhi() }}日</strong></div>
        </div>
        <div class="lunar-yiji">
          <div class="yi-row">
            <span class="yi-label">宜</span>
            <span class="yi-text">{{ selectedLunar.getDayYi().join('、') || '无' }}</span>
          </div>
          <div class="ji-row">
            <span class="ji-label">忌</span>
            <span class="ji-text">{{ selectedLunar.getDayJi().join('、') || '无' }}</span>
          </div>
        </div>
      </div>

      <!-- 遮罩层 -->
      <div class="overlay" :class="{ show: showDetail }" @click="closeDetail"></div>

      <!-- 详情面板 -->
      <div class="detail-panel" :class="{ show: showDetail }">
        <div class="detail-header">
          <h2 class="detail-title">{{ selectedDateDetail }}</h2>
          <button class="detail-close" @click="closeDetail" aria-label="关闭">
            <svg viewBox="0 0 24 24" width="24" height="24" fill="var(--text-primary)">
              <path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/>
            </svg>
          </button>
        </div>
        <div class="detail-content">
          <div class="detail-row">
            <span class="detail-label">公历</span>
            <span class="detail-value">{{ selectedDateDetail }}</span>
          </div>
          <div class="detail-row">
            <span class="detail-label">农历</span>
            <span class="detail-value">{{ selectedLunar.toString() }}</span>
          </div>
          <div class="detail-row">
            <span class="detail-label">生肖</span>
            <span class="detail-value">{{ selectedLunar.getYearShengXiao() }}</span>
          </div>
          <div class="detail-row">
            <span class="detail-label">干支</span>
            <span class="detail-value">{{ selectedLunar.getYearInGanZhi() }}年 {{ selectedLunar.getMonthInGanZhi() }}月 {{ selectedLunar.getDayInGanZhi() }}日</span>
          </div>
          <div class="detail-row">
            <span class="detail-label">宜</span>
            <span class="detail-value" style="color: var(--success)">{{ selectedLunar.getDayYi().join('、') || '无' }}</span>
          </div>
          <div class="detail-row">
            <span class="detail-label">忌</span>
            <span class="detail-value" style="color: var(--danger)">{{ selectedLunar.getDayJi().join('、') || '无' }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { Solar, Lunar } from 'lunar-javascript'

export default {
  name: 'App',
  data() {
    return {
      currentDate: new Date(),
      selectedDate: new Date(),
      theme: 'light',
      weekdays: ['日', '一', '二', '三', '四', '五', '六'],
      showDetail: false,
      holidays: this.loadHolidays()
    }
  },
  computed: {
    currentYear() {
      return this.currentDate.getFullYear()
    },
    currentMonth() {
      return this.currentDate.getMonth() + 1
    },
    calendarDays() {
      const year = this.currentYear
      const month = this.currentDate.getMonth()
      
      // 获取当月第一天是星期几
      const firstDay = new Date(year, month, 1)
      const startWeekday = firstDay.getDay()
      
      // 获取当月有多少天
      const daysInMonth = new Date(year, month + 1, 0).getDate()
      
      // 获取上个月有多少天
      const prevMonthDays = new Date(year, month, 0).getDate()
      
      const days = []
      
      // 添加上个月的日期
      for (let i = startWeekday - 1; i >= 0; i--) {
        const day = prevMonthDays - i
        const date = new Date(year, month - 1, day)
        days.push(this.createDayCell(date, false))
      }
      
      // 添加当月的日期
      for (let day = 1; day <= daysInMonth; day++) {
        const date = new Date(year, month, day)
        days.push(this.createDayCell(date, true))
      }
      
      // 添加下个月的日期（补齐 6 行）
      const remaining = 42 - days.length
      for (let day = 1; day <= remaining; day++) {
        const date = new Date(year, month + 1, day)
        days.push(this.createDayCell(date, false))
      }
      
      return days
    },
    selectedLunar() {
      const solar = Solar.fromDate(this.selectedDate)
      return solar.getLunar()
    },
    selectedDateDetail() {
      const year = this.selectedDate.getFullYear()
      const month = this.selectedDate.getMonth() + 1
      const day = this.selectedDate.getDate()
      return `${year}年${month}月${day}日`
    }
  },
  mounted() {
    // 初始化主题
    this.initTheme()
  },
  methods: {
    createDayCell(date, isCurrentMonth) {
      const today = new Date()
      const isToday = date.toDateString() === today.toDateString()
      const isSelected = date.toDateString() === this.selectedDate.toDateString()
      const isHoliday = this.isHoliday(date)
      
      const solar = Solar.fromDate(date)
      const lunar = solar.getLunar()
      
      return {
        date,
        day: date.getDate(),
        lunarDay: lunar.getDayInChinese(),
        isCurrentMonth,
        isToday,
        isSelected,
        isHoliday
      }
    },
    isHoliday(date) {
      const key = `${date.getMonth() + 1}-${date.getDate()}`
      return this.holidays.includes(key)
    },
    loadHolidays() {
      // 中国大陆主要法定节假日（不含调休）
      return [
        '1-1',  // 元旦
        '5-1',  // 劳动节
        '5-4',  // 青年节
        '6-1',  // 儿童节
        '10-1', // 国庆节
        '1-1'   // 春节（简化处理）
      ]
    },
    prevMonth() {
      this.currentDate = new Date(this.currentYear, this.currentMonth - 2, 1)
    },
    nextMonth() {
      this.currentDate = new Date(this.currentYear, this.currentMonth, 1)
    },
    selectDate(cell) {
      this.selectedDate = cell.date
      this.showDetail = true
    },
    closeDetail() {
      this.showDetail = false
    },
    getAriaLabel(cell) {
      const dateStr = `${cell.date.getFullYear()}年${cell.date.getMonth() + 1}月${cell.day}日`
      return `${dateStr}，农历${cell.lunarDay}${cell.isToday ? '，今天' : ''}`
    },
    initTheme() {
      const saved = localStorage.getItem('theme')
      if (saved) {
        this.theme = saved
      } else if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
        this.theme = 'dark'
      }
      document.documentElement.setAttribute('data-theme', this.theme)
      
      // 监听系统主题变化
      window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', (e) => {
        if (!localStorage.getItem('theme')) {
          this.theme = e.matches ? 'dark' : 'light'
          document.documentElement.setAttribute('data-theme', this.theme)
        }
      })
    },
    toggleTheme() {
      this.theme = this.theme === 'light' ? 'dark' : 'light'
      document.documentElement.setAttribute('data-theme', this.theme)
      localStorage.setItem('theme', this.theme)
    }
  }
}
</script>

<style scoped>
/* 组件级样式已在全局 styles.css 中定义 */
</style>
