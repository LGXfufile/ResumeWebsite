<script setup>
import { useI18n } from 'vue-i18n'
import LanguageSwitch from './components/LanguageSwitch.vue'

const { t } = useI18n()
</script>

<template>
  <el-config-provider>
    <el-container class="app-container">
      <el-header>
        <nav class="main-nav">
          <router-link to="/" class="nav-brand">{{ t('home.title') }}</router-link>
          <div class="nav-links">
            <router-link to="/about">{{ t('nav.about') }}</router-link>
            <router-link to="/experience">{{ t('nav.experience') }}</router-link>
            <router-link to="/projects">{{ t('nav.projects') }}</router-link>
            <router-link to="/contact">{{ t('nav.contact') }}</router-link>
            <LanguageSwitch />
          </div>
        </nav>
      </el-header>
      
      <el-main>
        <router-view v-slot="{ Component }">
          <transition name="fade" mode="out-in">
            <component :is="Component" />
          </transition>
        </router-view>
      </el-main>
      
      <el-footer>
        <div class="footer-content">
          <p>&copy; 2024 版权所有</p>
          <div class="social-links">
            <a href="#" target="_blank" title="GitHub"><i class="el-icon-github"></i></a>
            <a href="#" target="_blank" title="领英"><i class="el-icon-linkedin"></i></a>
            <a href="#" target="_blank" title="推特"><i class="el-icon-twitter"></i></a>
          </div>
        </div>
      </el-footer>
    </el-container>
  </el-config-provider>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=SF+Pro+Display:wght@300;400;500;600;700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+SC:wght@300;400;500;600;700&display=swap');

:root {
  --primary-color: #1d1d1f;
  --secondary-color: #0071e3;
  --text-color: #1d1d1f;
  --light-bg: #f5f5f7;
  --dark-bg: #000000;
  --white: #ffffff;
  --gray: #86868b;
  --transition: all 0.3s cubic-bezier(0.25, 0.1, 0.25, 1);
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Noto Sans SC', 'SF Pro Display', -apple-system, BlinkMacSystemFont, sans-serif;
  color: var(--text-color);
  line-height: 1.6;
  background-color: var(--light-bg);
}

.app-container {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.el-header {
  background-color: rgba(255, 255, 255, 0.8);
  backdrop-filter: saturate(180%) blur(20px);
  -webkit-backdrop-filter: saturate(180%) blur(20px);
  padding: 1rem 2rem;
  position: fixed;
  width: 100%;
  z-index: 1000;
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
  height: auto !important;
}

.main-nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0.5rem 0;
}

.nav-brand {
  color: var(--primary-color);
  font-size: 1.5rem;
  font-weight: 600;
  text-decoration: none;
  letter-spacing: -0.5px;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.nav-links {
  display: flex;
  align-items: center;
  gap: 2.5rem;
}

.nav-links a {
  color: var(--gray);
  text-decoration: none;
  font-weight: 500;
  font-size: 1rem;
  transition: var(--transition);
  position: relative;
  padding: 0.5rem 0;
}

.nav-links a:hover,
.nav-links a.router-link-active {
  color: var(--primary-color);
}

.nav-links a::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background-color: var(--secondary-color);
  transition: var(--transition);
}

.nav-links a:hover::after,
.nav-links a.router-link-active::after {
  width: 100%;
}

.el-main {
  padding-top: 80px;
  flex: 1;
  background-color: var(--light-bg);
}

.el-footer {
  background-color: var(--dark-bg);
  color: var(--white);
  padding: 3rem 0;
  margin-top: auto;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 2rem;
}

.footer-content p {
  font-size: 0.9rem;
  opacity: 0.8;
}

.social-links {
  display: flex;
  gap: 1.5rem;
}

.social-links a {
  color: var(--white);
  font-size: 1.2rem;
  transition: var(--transition);
  opacity: 0.8;
}

.social-links a:hover {
  color: var(--secondary-color);
  opacity: 1;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* 滚动条样式 */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: var(--light-bg);
}

::-webkit-scrollbar-thumb {
  background: var(--gray);
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: var(--primary-color);
}

@media (max-width: 768px) {
  .el-header {
    padding: 0.5rem 1rem;
  }

  .main-nav {
    flex-direction: column;
    gap: 1rem;
  }

  .nav-links {
    flex-wrap: wrap;
    justify-content: center;
    gap: 1.5rem;
  }

  .nav-links a {
    font-size: 0.9rem;
  }

  .footer-content {
    flex-direction: column;
    gap: 1.5rem;
    text-align: center;
  }
}
</style>
