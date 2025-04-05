<template>
  <div class="home">
    <el-row class="hero-section">
      <el-col :span="12" class="hero-content">
        <h1>{{ t('home.title') }} <span class="highlight">Your Name</span></h1>
        <h2>{{ t('home.subtitle') }}</h2>
        <p class="description">
          {{ t('home.description') }}
        </p>
        <div class="cta-buttons">
          <el-button type="primary" size="large" @click="$router.push('/contact')">
            {{ t('home.contact') }}
          </el-button>
          <el-button size="large" @click="$router.push('/projects')">
            {{ t('home.viewProjects') }}
          </el-button>
        </div>
      </el-col>
      <el-col :span="12" class="hero-image">
        <img src="../assets/1.jpg" alt="Professional Image">
      </el-col>
    </el-row>

    <el-row class="skills-section">
      <el-col :span="24">
        <h2 class="section-title">{{ t('home.coreSkills') }}</h2>
        <div class="skills-grid">
          <el-card v-for="skill in skills" :key="skill.name" class="skill-card">
            <template #header>
              <div class="skill-header">
                <el-icon :size="30"><component :is="skill.icon" /></el-icon>
                <h3>{{ skill.name }}</h3>
              </div>
            </template>
            <p>{{ skill.description }}</p>
          </el-card>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script setup>
import { useI18n } from 'vue-i18n'

const { t } = useI18n()

const skills = [
  {
    name: '网页开发',
    icon: 'Monitor',
    description: '精通现代网页技术和框架开发'
  },
  {
    name: '界面设计',
    icon: 'Brush',
    description: '创造美观直观的用户界面'
  },
  {
    name: '项目管理',
    icon: 'Setting',
    description: '领导团队按时交付高质量项目'
  },
  {
    name: '问题解决',
    icon: 'Lightning',
    description: '为复杂挑战找到创新解决方案'
  }
]
</script>

<style scoped>
.home {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
}

.hero-section {
  min-height: calc(100vh - 80px);
  display: flex;
  align-items: center;
  margin-bottom: 6rem;
  position: relative;
  padding: 2rem 0;
}

.hero-content {
  padding-right: 4rem;
  position: relative;
  z-index: 1;
}

.hero-content h1 {
  font-size: 4rem;
  margin-bottom: 1.5rem;
  line-height: 1.2;
  font-weight: 700;
  letter-spacing: -1px;
  background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.highlight {
  color: var(--secondary-color);
  -webkit-text-fill-color: var(--secondary-color);
  position: relative;
  display: inline-block;
}

.highlight::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 8px;
  background-color: rgba(0, 113, 227, 0.2);
  z-index: -1;
}

.hero-content h2 {
  font-size: 2.5rem;
  color: var(--gray);
  margin-bottom: 2rem;
  font-weight: 500;
}

.description {
  font-size: 1.2rem;
  margin-bottom: 3rem;
  color: var(--gray);
  line-height: 1.8;
  max-width: 600px;
}

.cta-buttons {
  display: flex;
  gap: 1.5rem;
}

.cta-buttons .el-button {
  padding: 1rem 2rem;
  font-size: 1.1rem;
  border-radius: 30px;
  transition: var(--transition);
  font-weight: 500;
}

.cta-buttons .el-button--primary {
  background-color: var(--secondary-color);
  border-color: var(--secondary-color);
  box-shadow: 0 10px 20px rgba(0, 113, 227, 0.2);
}

.cta-buttons .el-button--primary:hover {
  background-color: #0077ed;
  transform: translateY(-2px);
  box-shadow: 0 15px 30px rgba(0, 113, 227, 0.3);
}

.cta-buttons .el-button--default {
  background-color: rgba(255, 255, 255, 0.8);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border-color: var(--gray);
  color: var(--gray);
}

.cta-buttons .el-button--default:hover {
  background-color: var(--white);
  color: var(--primary-color);
  border-color: var(--primary-color);
  transform: translateY(-2px);
}

.hero-image {
  position: relative;
}

.hero-image img {
  width: 100%;
  border-radius: 30px;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
  transform: perspective(1000px) rotateY(-5deg);
  transition: var(--transition);
}

.hero-image:hover img {
  transform: perspective(1000px) rotateY(0deg);
}

.skills-section {
  padding: 6rem 0;
  background-color: var(--white);
  border-radius: 40px;
  margin: 0 -2rem;
}

.section-title {
  text-align: center;
  margin-bottom: 4rem;
  font-size: 3rem;
  font-weight: 600;
  color: var(--primary-color);
  position: relative;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 60px;
  height: 3px;
  background-color: var(--secondary-color);
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2.5rem;
  padding: 0 2rem;
}

.skill-card {
  height: 100%;
  transition: var(--transition);
  background-color: var(--light-bg);
  border: none;
  border-radius: 20px;
  overflow: hidden;
}

.skill-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
}

.skill-header {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1.5rem;
  background-color: rgba(0, 113, 227, 0.05);
}

.skill-header h3 {
  margin: 0;
  font-size: 1.3rem;
  font-weight: 500;
  color: var(--primary-color);
}

.skill-card :deep(.el-card__body) {
  padding: 1.5rem;
}

.skill-card p {
  color: var(--gray);
  line-height: 1.8;
  margin: 0;
}

@media (max-width: 768px) {
  .home {
    padding: 1rem;
  }

  .hero-section {
    flex-direction: column;
    text-align: center;
    min-height: auto;
    padding: 4rem 1rem;
  }

  .hero-content {
    padding-right: 0;
    margin-bottom: 3rem;
  }

  .hero-content h1 {
    font-size: 3rem;
  }

  .hero-content h2 {
    font-size: 2rem;
  }

  .description {
    font-size: 1.1rem;
    margin: 0 auto 2rem;
  }

  .cta-buttons {
    justify-content: center;
    flex-wrap: wrap;
  }

  .hero-image {
    margin-top: 2rem;
  }

  .hero-image img {
    transform: none;
  }

  .skills-section {
    margin: 0 -1rem;
    padding: 4rem 0;
    border-radius: 30px;
  }

  .section-title {
    font-size: 2.5rem;
    margin-bottom: 3rem;
  }

  .skills-grid {
    padding: 0 1rem;
    gap: 1.5rem;
  }
}
</style> 