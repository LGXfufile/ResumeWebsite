<template>
  <div class="projects">
    <el-row>
      <el-col :span="24">
        <h2 class="section-title">Featured Projects</h2>
        <div class="projects-grid">
          <el-card
            v-for="project in projects"
            :key="project.id"
            class="project-card"
            :body-style="{ padding: '0px' }"
          >
            <img :src="project.image" class="project-image" :alt="project.title">
            <div class="project-info">
              <h3>{{ project.title }}</h3>
              <p class="project-description">{{ project.description }}</p>
              <div class="project-tags">
                <el-tag
                  v-for="tag in project.tags"
                  :key="tag"
                  size="small"
                  class="project-tag"
                >
                  {{ tag }}
                </el-tag>
              </div>
              <div class="project-links">
                <el-button
                  v-if="project.demo"
                  type="primary"
                  size="small"
                  @click="openLink(project.demo)"
                >
                  Live Demo
                </el-button>
                <el-button
                  v-if="project.github"
                  type="info"
                  size="small"
                  @click="openLink(project.github)"
                >
                  GitHub
                </el-button>
              </div>
            </div>
          </el-card>
        </div>
      </el-col>
    </el-row>

    <el-row class="testimonials-section">
      <el-col :span="24">
        <h2 class="section-title">Client Testimonials</h2>
        <el-carousel :interval="4000" type="card" height="300px">
          <el-carousel-item v-for="testimonial in testimonials" :key="testimonial.id">
            <el-card class="testimonial-card">
              <div class="testimonial-content">
                <p class="testimonial-text">"{{ testimonial.text }}"</p>
                <div class="testimonial-author">
                  <img :src="testimonial.avatar" :alt="testimonial.name" class="author-avatar">
                  <div class="author-info">
                    <h4>{{ testimonial.name }}</h4>
                    <p>{{ testimonial.position }}</p>
                  </div>
                </div>
              </div>
            </el-card>
          </el-carousel-item>
        </el-carousel>
      </el-col>
    </el-row>
  </div>
</template>

<script setup>
const projects = [
  {
    id: 1,
    title: 'E-commerce Platform',
    description: 'A full-stack e-commerce platform with real-time inventory management and payment processing.',
    image: '../assets/1.jpg',
    tags: ['Vue.js', 'Node.js', 'MongoDB', 'Stripe'],
    demo: 'https://demo.example.com',
    github: 'https://github.com/username/project1'
  },
  {
    id: 2,
    title: 'Task Management App',
    description: 'A collaborative task management application with real-time updates and team features.',
    image: '../assets/2.jpg',
    tags: ['React', 'Firebase', 'Redux'],
    demo: 'https://demo.example.com',
    github: 'https://github.com/username/project2'
  },
  {
    id: 3,
    title: 'AI-Powered Analytics Dashboard',
    description: 'A data visualization dashboard with machine learning insights and predictive analytics.',
    image: '../assets/3.jpg',
    tags: ['Python', 'TensorFlow', 'D3.js'],
    demo: 'https://demo.example.com',
    github: 'https://github.com/username/project3'
  }
]

const testimonials = [
  {
    id: 1,
    text: 'Working with this developer was an absolute pleasure. Their attention to detail and problem-solving skills are exceptional.',
    name: 'John Smith',
    position: 'CEO, Tech Company',
    avatar: '../assets/1.jpg'
  },
  {
    id: 2,
    text: 'The project was delivered on time and exceeded our expectations. The code quality and documentation were outstanding.',
    name: 'Sarah Johnson',
    position: 'Product Manager, Startup',
    avatar: '../assets/2.jpg'
  },
  {
    id: 3,
    text: 'A true professional who consistently delivers high-quality work. Their technical expertise is matched by their excellent communication skills.',
    name: 'Michael Brown',
    position: 'CTO, Enterprise Solutions',
    avatar: '../assets/3.jpg'
  }
]

const openLink = (url) => {
  window.open(url, '_blank')
}
</script>

<style scoped>
.projects {
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

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin-bottom: 4rem;
}

.project-card {
  transition: transform 0.3s ease;
}

.project-card:hover {
  transform: translateY(-5px);
}

.project-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
}

.project-info {
  padding: 1.5rem;
}

.project-info h3 {
  margin: 0 0 1rem 0;
  font-size: 1.5rem;
}

.project-description {
  color: #666;
  margin-bottom: 1rem;
  line-height: 1.6;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.project-links {
  display: flex;
  gap: 1rem;
}

.testimonials-section {
  margin-top: 4rem;
}

.testimonial-card {
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.testimonial-content {
  padding: 2rem;
  text-align: center;
}

.testimonial-text {
  font-size: 1.2rem;
  line-height: 1.8;
  margin-bottom: 2rem;
  color: #666;
}

.testimonial-author {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
}

.author-avatar {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  object-fit: cover;
}

.author-info h4 {
  margin: 0;
  font-size: 1.1rem;
}

.author-info p {
  margin: 0;
  color: #666;
}

@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }

  .testimonial-content {
    padding: 1rem;
  }
}
</style> 