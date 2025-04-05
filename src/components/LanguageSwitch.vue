<template>
  <div class="language-switch">
    <el-dropdown trigger="click" @command="handleCommand">
      <span class="el-dropdown-link">
        {{ currentLanguage === 'en' ? 'English' : '中文' }}
        <el-icon class="el-icon--right"><arrow-down /></el-icon>
      </span>
      <template #dropdown>
        <el-dropdown-menu>
          <el-dropdown-item command="en">English</el-dropdown-item>
          <el-dropdown-item command="zh">中文</el-dropdown-item>
        </el-dropdown-menu>
      </template>
    </el-dropdown>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { ArrowDown } from '@element-plus/icons-vue'
import { useI18n } from 'vue-i18n'

const { locale } = useI18n()
const currentLanguage = ref(locale.value)

const handleCommand = (command) => {
  locale.value = command
  currentLanguage.value = command
}
</script>

<style scoped>
.language-switch {
  margin-left: 2rem;
}

.el-dropdown-link {
  cursor: pointer;
  color: var(--gray);
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.9rem;
  transition: var(--transition);
}

.el-dropdown-link:hover {
  color: var(--primary-color);
}

.el-icon--right {
  margin-left: 0.5rem;
}
</style> 