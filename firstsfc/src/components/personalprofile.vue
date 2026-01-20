<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
    <div class="container">
      <a class="navbar-brand" href="#home" @click="scrollTo('home')">My Profile</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ms-auto align-items-center">
          <li class="nav-item"><a class="nav-link" href="#about" @click="scrollTo('about')">About</a></li>
          <li class="nav-item"><a class="nav-link" href="#skills" @click="scrollTo('skills')">Skills</a></li>
          <li class="nav-item"><a class="nav-link" href="#contact" @click="scrollTo('contact')">Contact</a></li>
          <li class="nav-item ms-lg-3">
            <button id="modeBtn" class="btn btn-outline-light btn-sm" @click="toggleMode">
              {{ isDarkMode ? '☀️ Light Mode' : '🌙 Dark Mode' }}
            </button>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <div class="container mt-5 pt-5">
    <header id="home" class="text-center mb-5 py-4" :class="{ 'dark-section': isDarkMode }">
      <img src="picture.jpg" alt="Profile" class="profile-img mb-3">
      <h1 class="fw-bolder">Cristian R. Saldua</h1>
      <p class="lead">IT Student | Aspiring Developer</p>
      <p id="bio" class="mt-3 mx-auto w-75">
        I am a 2nd-year IT student at Asia Pacific College.
      </p>
    </header>

    <section id="about" class="py-4">
      <h2 class="mb-4">About Me</h2>
      <div class="row g-4">
        <div class="col-md-6">
          <div class="card h-100" :class="isDarkMode ? 'dark-section' : 'light-card'">
            <div class="card-body">
              <h5 class="card-title">🎓 Education</h5>
              <p class="mb-1"><strong>BS in Information Technology</strong></p>
              <p class="small">Asia Pacific College (2024 - Present)</p>
              <p class="mb-1"><strong>Senior High School (STEM-IT)</strong></p>
              <p class="small">Asia Pacific College</p>
            </div>
          </div>
        </div>
        <div class="col-md-6">
          <div class="card h-100" :class="isDarkMode ? 'dark-section' : 'light-card'">
            <div class="card-body">
              <h5 class="card-title">✨ Quotes</h5>
              <p class="mt-3" style="font-style: italic;">
                "Whenever you want to achieve something, keep your eyes open, concentrate and make sure you know exactly what it is you want. No one can hit their target with their eyes closed." - Paulo Coelho
              </p>
            </div>
          </div>
        </div>
        <div class="col-md-6">
          <div class="card h-100" :class="isDarkMode ? 'dark-section' : 'light-card'">
            <div class="card-body">
              <h5 class="card-title">🎮 Hobbies</h5>
              <p>In my free time, I often play with my friends. I also read manga and manhwas to pass time.</p>
            </div>
          </div>
        </div>
        <div class="col-md-6">
          <div class="card h-100" :class="isDarkMode ? 'dark-section' : 'light-card'">
            <div class="card-body">
              <h5 class="card-title">🚀 Future Goals</h5>
              <p>My goal is to finish my education and find a job to have a stable life in the future.</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="skills" class="py-4">
      <h2 class="mb-4">Skills</h2>
      <div class="row g-3 text-center">
        <div v-for="skill in skills" :key="skill.name" class="col-6 col-md-3">
          <div class="card h-100 skill-card-static" :class="isDarkMode ? 'dark-section' : 'light-card'">
            <div class="card-body">
              <div class="mb-2" style="font-size: 2rem;">{{ skill.icon }}</div>
              <h6 class="fw-bold mb-0">{{ skill.name }}</h6>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="contact" class="pb-5">
      <div class="row justify-content-center">
        <div class="col-md-8">
          <div class="card" :class="isDarkMode ? 'dark-section' : 'light-card'">
            <div class="card-body p-4">
              <h2 class="h4 mb-4 text-center">Get In Touch</h2>
              <form @submit.prevent="submitForm">
                <div class="row g-3">
                  <div class="col-md-6">
                    <label class="form-label small">Your Name</label>
                    <input v-model="form.name" type="text" class="form-control custom-input" placeholder="Name" required>
                  </div>
                  <div class="col-md-6">
                    <label class="form-label small">Email Address</label>
                    <input v-model="form.email" type="email" class="form-control custom-input" placeholder="email@example.com" required>
                  </div>
                  <div class="col-12">
                    <label class="form-label small">Message</label>
                    <textarea v-model="form.message" class="form-control custom-input" rows="4" placeholder="Message..."></textarea>
                  </div>
                  <div class="col-12 mt-4">
                    <button class="btn btn-primary w-100 py-2 fw-bold">Send Message</button>
                  </div>
                </div>
              </form>
              <p v-if="formMessage" id="formMsg" class="mt-3 text-center fw-bold text-success">{{ formMessage }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>

  <footer class="py-4 bg-black text-center text-white">
    <div class="container small">© 2026 Cristian Saldua | My Profile</div>
  </footer>
</template>

<script setup>
import { ref, reactive, onMounted } from 'vue'

const isDarkMode = ref(true)
const formMessage = ref('')
const form = reactive({
  name: '',
  email: '',
  message: ''
})

const skills = [
  { name: 'HTML', icon: '🌐' },
  { name: 'CSS', icon: '🎨' },
  { name: 'JavaScript', icon: '⚡' },
  { name: 'Python', icon: '🐍' }
]

const toggleMode = () => {
  isDarkMode.value = !isDarkMode.value
  document.body.classList.toggle('light-mode')
}

const submitForm = () => {
  formMessage.value = 'Success! Message Received.'
  form.name = form.email = form.message = ''
  setTimeout(() => formMessage.value = '', 3000)
}

const scrollTo = (id) => {
  document.getElementById(id).scrollIntoView({ behavior: 'smooth' })
}

onMounted(() => {
  const saved = localStorage.getItem('darkMode')
  if (saved === 'light') {
    isDarkMode.value = false
    document.body.classList.add('light-mode')
  }
})

defineExpose({ toggleMode })
</script>

<style src="./css/personalprofile.css"></style>
<style src="./css/style.css"></style>