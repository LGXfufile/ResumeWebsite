<template>
  <div class="about">
    <el-row class="about-section">
      <el-col :span="12" class="about-image">
        <img src="../assets/2.jpg" alt="About Me">
      </el-col>
      <el-col :span="12" class="about-content">
        <h2 class="section-title">{{ t('about.title') }}</h2>
        <p class="about-text">
          {{ t('about.description1') }}
        </p>
        <p class="about-text">
          {{ t('about.description2') }}
        </p>
        <div class="personal-info">
          <el-descriptions :column="1" border>
            <el-descriptions-item :label="t('contact.form.name')">Your Name</el-descriptions-item>
            <el-descriptions-item :label="t('contact.form.email')">your.email@example.com</el-descriptions-item>
            <el-descriptions-item label="Phone">+1 (123) 456-7890</el-descriptions-item>
          </el-descriptions>
        </div>
      </el-col>
    </el-row>

    <el-row class="education-section">
      <el-col :span="24">
        <h2 class="section-title">{{ t('about.education') }}</h2>
        <el-timeline>
          <el-timeline-item
            v-for="(education, index) in educationHistory"
            :key="index"
            :timestamp="education.year"
            :type="education.type"
          >
            <h3>{{ education.degree }}</h3>
            <p>{{ education.institution }}</p>
            <p>{{ education.description }}</p>
          </el-timeline-item>
        </el-timeline>
      </el-col>
    </el-row>
  </div>
</template>

<script setup>
import { useI18n } from 'vue-i18n'

const { t } = useI18n()

const educationHistory = [
  {
    year: '2015 - 2019',
    type: 'primary',
    degree: 'Bachelor of Science in Computer Science',
    institution: 'University Name',
    description: 'Graduated with honors. Specialized in Software Engineering and Data Structures.'
  },
  {
    year: '2019 - 2021',
    type: 'success',
    degree: 'Master of Science in Information Technology',
    institution: 'University Name',
    description: 'Focus on Advanced Web Technologies and Cloud Computing.'
  }
]
</script>

<style scoped>
.about {
  max-width: 1200px;
  margin: 0 auto;
  padding: 4rem 2rem;
}

.about-section {
  margin-bottom: 6rem;
  display: flex;
  align-items: center;
}

.about-image {
  position: relative;
}

.about-image img {
  width: 100%;
  border-radius: 30px;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
  transform: perspective(1000px) rotateY(5deg);
  transition: var(--transition);
}

.about-image:hover img {
  transform: perspective(1000px) rotateY(0deg);
}

.about-content {
  padding-left: 4rem;
}

.section-title {
  font-size: 3rem;
  margin-bottom: 2.5rem;
  color: var(--primary-color);
  font-weight: 600;
  position: relative;
  display: inline-block;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 0;
  width: 60px;
  height: 3px;
  background-color: var(--secondary-color);
}

.about-text {
  font-size: 1.2rem;
  line-height: 1.8;
  margin-bottom: 2rem;
  color: var(--gray);
}

.personal-info {
  margin-top: 3rem;
}

.personal-info :deep(.el-descriptions) {
  background-color: var(--white);
  border-radius: 20px;
  padding: 2rem;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
}

.personal-info :deep(.el-descriptions__label) {
  color: var(--gray);
  font-weight: 500;
}

.personal-info :deep(.el-descriptions__content) {
  color: var(--primary-color);
  font-weight: 500;
}

.education-section {
  margin-top: 6rem;
}

.education-section .section-title {
  display: block;
  text-align: center;
}

.education-section .section-title::after {
  left: 50%;
  transform: translateX(-50%);
}

.education-section :deep(.el-timeline) {
  padding: 2rem 0;
}

.education-section :deep(.el-timeline-item__node) {
  background-color: var(--secondary-color);
  border-color: var(--secondary-color);
}

.education-section :deep(.el-timeline-item__timestamp) {
  color: var(--gray);
  font-size: 1rem;
}

.education-section h3 {
  font-size: 1.5rem;
  color: var(--primary-color);
  margin-bottom: 0.5rem;
}

.education-section p {
  color: var(--gray);
  line-height: 1.8;
  margin-bottom: 0.5rem;
}

@media (max-width: 768px) {
  .about {
    padding: 2rem 1rem;
  }

  .about-section {
    flex-direction: column;
    margin-bottom: 4rem;
  }

  .about-content {
    padding-left: 0;
    margin-top: 2rem;
  }

  .about-image {
    margin-bottom: 2rem;
  }

  .about-image img {
    transform: none;
  }

  .section-title {
    font-size: 2.5rem;
  }

  .about-text {
    font-size: 1.1rem;
  }
}
</style> 