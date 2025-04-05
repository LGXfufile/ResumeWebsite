<template>
  <div class="contact">
    <el-row>
      <el-col :span="24">
        <h2 class="section-title">Get in Touch</h2>
        <p class="section-subtitle">I'd love to hear from you! Feel free to reach out for any inquiries or opportunities.</p>
      </el-col>
    </el-row>

    <el-row :gutter="40">
      <el-col :xs="24" :sm="12" :md="12">
        <el-form
          ref="contactForm"
          :model="form"
          :rules="rules"
          label-position="top"
          class="contact-form"
        >
          <el-form-item label="Name" prop="name">
            <el-input v-model="form.name" placeholder="Your name"></el-input>
          </el-form-item>
          
          <el-form-item label="Email" prop="email">
            <el-input v-model="form.email" placeholder="Your email"></el-input>
          </el-form-item>
          
          <el-form-item label="Subject" prop="subject">
            <el-input v-model="form.subject" placeholder="Subject"></el-input>
          </el-form-item>
          
          <el-form-item label="Message" prop="message">
            <el-input
              v-model="form.message"
              type="textarea"
              :rows="6"
              placeholder="Your message"
            ></el-input>
          </el-form-item>
          
          <el-form-item>
            <el-button type="primary" @click="submitForm" :loading="loading">
              Send Message
            </el-button>
          </el-form-item>
        </el-form>
      </el-col>

      <el-col :xs="24" :sm="12" :md="12">
        <div class="contact-info">
          <div class="info-card">
            <el-icon :size="30"><Location /></el-icon>
            <h3>Location</h3>
            <p>Your City, Country</p>
          </div>
          
          <div class="info-card">
            <el-icon :size="30"><Message /></el-icon>
            <h3>Email</h3>
            <p>your.email@example.com</p>
          </div>
          
          <div class="info-card">
            <el-icon :size="30"><Phone /></el-icon>
            <h3>Phone</h3>
            <p>+1 (123) 456-7890</p>
          </div>
          
          <div class="social-links">
            <a href="#" target="_blank" class="social-link">
              <el-icon :size="24"><Github /></el-icon>
            </a>
            <a href="#" target="_blank" class="social-link">
              <el-icon :size="24"><Linkedin /></el-icon>
            </a>
            <a href="#" target="_blank" class="social-link">
              <el-icon :size="24"><Twitter /></el-icon>
            </a>
          </div>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'
import { ElMessage } from 'element-plus'

const contactForm = ref(null)
const loading = ref(false)

const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const rules = {
  name: [
    { required: true, message: 'Please enter your name', trigger: 'blur' },
    { min: 2, message: 'Name must be at least 2 characters', trigger: 'blur' }
  ],
  email: [
    { required: true, message: 'Please enter your email', trigger: 'blur' },
    { type: 'email', message: 'Please enter a valid email', trigger: 'blur' }
  ],
  subject: [
    { required: true, message: 'Please enter a subject', trigger: 'blur' }
  ],
  message: [
    { required: true, message: 'Please enter your message', trigger: 'blur' },
    { min: 10, message: 'Message must be at least 10 characters', trigger: 'blur' }
  ]
}

const submitForm = async () => {
  if (!contactForm.value) return
  
  try {
    await contactForm.value.validate()
    loading.value = true
    
    // Simulate API call
    await new Promise(resolve => setTimeout(resolve, 1000))
    
    ElMessage.success('Message sent successfully!')
    form.name = ''
    form.email = ''
    form.subject = ''
    form.message = ''
  } catch (error) {
    console.error('Form validation failed:', error)
  } finally {
    loading.value = false
  }
}
</script>

<style scoped>
.contact {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
}

.section-title {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  color: var(--primary-color);
  text-align: center;
}

.section-subtitle {
  text-align: center;
  color: #666;
  margin-bottom: 3rem;
  font-size: 1.1rem;
}

.contact-form {
  background: white;
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.info-card {
  background: white;
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  text-align: center;
  transition: transform 0.3s ease;
}

.info-card:hover {
  transform: translateY(-5px);
}

.info-card h3 {
  margin: 1rem 0;
  color: var(--primary-color);
}

.info-card p {
  color: #666;
  margin: 0;
}

.social-links {
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  margin-top: 1rem;
}

.social-link {
  color: var(--primary-color);
  transition: color 0.3s ease;
}

.social-link:hover {
  color: var(--secondary-color);
}

@media (max-width: 768px) {
  .contact-form {
    margin-bottom: 2rem;
  }
}
</style> 