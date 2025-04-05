<template>
  <div class="experience">
    <el-row>
      <el-col :span="24">
        <h2 class="section-title">Professional Experience</h2>
        <el-timeline>
          <el-timeline-item
            v-for="(job, index) in workExperience"
            :key="index"
            :timestamp="job.period"
            :type="job.type"
            placement="top"
          >
            <el-card class="experience-card">
              <template #header>
                <div class="job-header">
                  <h3>{{ job.position }}</h3>
                  <span class="company">{{ job.company }}</span>
                </div>
              </template>
              <div class="job-description">
                <p>{{ job.description }}</p>
                <div class="responsibilities">
                  <h4>Key Responsibilities:</h4>
                  <ul>
                    <li v-for="(responsibility, idx) in job.responsibilities" :key="idx">
                      {{ responsibility }}
                    </li>
                  </ul>
                </div>
                <div class="achievements" v-if="job.achievements">
                  <h4>Key Achievements:</h4>
                  <ul>
                    <li v-for="(achievement, idx) in job.achievements" :key="idx">
                      {{ achievement }}
                    </li>
                  </ul>
                </div>
              </div>
            </el-card>
          </el-timeline-item>
        </el-timeline>
      </el-col>
    </el-row>

    <el-row class="skills-section">
      <el-col :span="24">
        <h2 class="section-title">Technical Skills</h2>
        <div class="skills-container">
          <el-card v-for="(category, index) in technicalSkills" :key="index" class="skill-category">
            <template #header>
              <div class="category-header">
                <el-icon :size="24"><component :is="category.icon" /></el-icon>
                <h3>{{ category.name }}</h3>
              </div>
            </template>
            <div class="skills-list">
              <el-tag
                v-for="(skill, idx) in category.skills"
                :key="idx"
                :type="skill.type"
                class="skill-tag"
              >
                {{ skill.name }}
              </el-tag>
            </div>
          </el-card>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script setup>
const workExperience = [
  {
    period: '2021 - Present',
    type: 'primary',
    position: 'Senior Software Engineer',
    company: 'Tech Company Inc.',
    description: 'Leading development teams and implementing innovative solutions for enterprise clients.',
    responsibilities: [
      'Lead a team of 5 developers in implementing new features',
      'Design and implement scalable microservices architecture',
      'Conduct code reviews and mentor junior developers',
      'Collaborate with product managers to define requirements'
    ],
    achievements: [
      'Reduced system response time by 40% through optimization',
      'Successfully migrated legacy system to modern architecture',
      'Implemented CI/CD pipeline reducing deployment time by 60%'
    ]
  },
  {
    period: '2019 - 2021',
    type: 'success',
    position: 'Software Engineer',
    company: 'Startup Solutions',
    description: 'Developed and maintained web applications using modern technologies.',
    responsibilities: [
      'Developed and maintained frontend applications',
      'Implemented RESTful APIs',
      'Optimized database queries and performance',
      'Participated in agile development process'
    ]
  }
]

const technicalSkills = [
  {
    name: 'Frontend',
    icon: 'Monitor',
    skills: [
      { name: 'Vue.js', type: 'success' },
      { name: 'React', type: 'success' },
      { name: 'JavaScript', type: 'warning' },
      { name: 'HTML5', type: 'info' },
      { name: 'CSS3', type: 'info' }
    ]
  },
  {
    name: 'Backend',
    icon: 'Setting',
    skills: [
      { name: 'Node.js', type: 'success' },
      { name: 'Python', type: 'warning' },
      { name: 'Java', type: 'danger' },
      { name: 'SQL', type: 'info' },
      { name: 'MongoDB', type: 'info' }
    ]
  },
  {
    name: 'DevOps',
    icon: 'Cloudy',
    skills: [
      { name: 'Docker', type: 'success' },
      { name: 'Kubernetes', type: 'warning' },
      { name: 'AWS', type: 'danger' },
      { name: 'CI/CD', type: 'info' }
    ]
  }
]
</script>

<style scoped>
.experience {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
}

.section-title {
  font-size: 2.5rem;
  margin-bottom: 2rem;
  color: var(--primary-color);
  text-align: center;
}

.experience-card {
  margin-bottom: 1rem;
}

.job-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.job-header h3 {
  margin: 0;
  font-size: 1.5rem;
}

.company {
  color: var(--secondary-color);
  font-weight: 500;
}

.job-description {
  margin-top: 1rem;
}

.job-description p {
  margin-bottom: 1rem;
  line-height: 1.6;
}

.responsibilities,
.achievements {
  margin-top: 1rem;
}

.responsibilities h4,
.achievements h4 {
  margin-bottom: 0.5rem;
  color: var(--primary-color);
}

.responsibilities ul,
.achievements ul {
  padding-left: 1.5rem;
}

.responsibilities li,
.achievements li {
  margin-bottom: 0.5rem;
  line-height: 1.6;
}

.skills-section {
  margin-top: 4rem;
}

.skills-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.skill-category {
  height: 100%;
}

.category-header {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.category-header h3 {
  margin: 0;
}

.skills-list {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.skill-tag {
  margin: 0.25rem;
}

@media (max-width: 768px) {
  .job-header {
    flex-direction: column;
    align-items: flex-start;
  }

  .company {
    margin-top: 0.5rem;
  }
}
</style> 