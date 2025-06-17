<template>
  <div class="portfolio-container">
    <header class="hero-section py-5">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-md-8">
            <h1 class="display-4 fw-bold mb-3">Hi, I'm <span class="text-primary">Your Name</span></h1>
            <h2 class="h3 text-secondary mb-4">Software Engineer</h2>
            <p class="lead mb-4">
              I build elegant solutions to complex problems. Specializing in full-stack development
              with a passion for creating intuitive user experiences.
            </p>
            <div class="d-flex gap-3">
              <a href="#contact" class="btn btn-primary">Get in Touch</a>
              <a href="#projects" class="btn btn-outline-primary">View Projects</a>
            </div>
          </div>
        </div>
      </div>
    </header>

    <section id="about" class="py-5">
      <div class="container">
        <h2 class="section-title mb-4">About Me</h2>
        <div class="row">
          <div class="col-md-6">
            <p class="mb-4">
              I'm a software engineer with X years of experience in building web applications
              and software solutions. My expertise includes:
            </p>
            <ul class="skills-list">
              <li>Frontend Development (Vue.js, React, JavaScript/TypeScript)</li>
              <li>Backend Development (Node.js, Python)</li>
              <li>Database Design & Management</li>
              <li>Cloud Services & DevOps</li>
            </ul>
          </div>
          <div class="col-md-6">
            <div class="card">
              <div class="card-body">
                <h3 class="h5 mb-3">Quick Facts</h3>
                <ul class="list-unstyled">
                  <li class="mb-2">📍 Location: Your Location</li>
                  <li class="mb-2">🎓 Education: Your Degree</li>
                  <li class="mb-2">💼 Experience: X years</li>
                  <li class="mb-2">🌐 Languages: Your Languages</li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="projects" class="py-5 bg-light">
      <div class="container">
        <h2 class="section-title mb-4">Featured Projects</h2>
        <div class="row g-4">
          <div class="col-md-6 col-lg-4" v-for="project in projects" :key="project.id">
            <div class="card h-100">
              <div class="card-body">
                <h3 class="h5 card-title">{{ project.title }}</h3>
                <p class="card-text">{{ project.description }}</p>
                <div class="d-flex gap-2 mb-3">
                  <span v-for="tech in project.technologies" :key="tech" 
                        class="badge bg-primary">{{ tech }}</span>
                </div>
                <a :href="project.link" class="btn btn-outline-primary btn-sm" target="_blank">
                  View Project
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="contact" class="py-5">
      <div class="container">
        <h2 class="section-title mb-4">Get in Touch</h2>
        <div class="row justify-content-center">
          <div class="col-md-8">
            <div class="card">
              <div class="card-body">
                <div class="d-flex justify-content-center gap-4 mb-4">
                  <a href="https://github.com/yourusername" class="text-dark" target="_blank">
                    <i class="bi bi-github fs-3"></i>
                  </a>
                  <a href="https://linkedin.com/in/yourusername" class="text-dark" target="_blank">
                    <i class="bi bi-linkedin fs-3"></i>
                  </a>
                  <a href="mailto:your.email@example.com" class="text-dark">
                    <i class="bi bi-envelope fs-3"></i>
                  </a>
                </div>
                <p class="text-center mb-0">
                  I'm always open to discussing new projects, creative ideas, or opportunities to be part of your vision.
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const projects = ref([
  {
    id: 1,
    title: 'Project One',
    description: 'A brief description of your first project and its impact.',
    technologies: ['Vue.js', 'Node.js', 'MongoDB'],
    link: '#'
  },
  {
    id: 2,
    title: 'Project Two',
    description: 'Description of your second project highlighting key features.',
    technologies: ['React', 'Python', 'PostgreSQL'],
    link: '#'
  },
  {
    id: 3,
    title: 'Project Three',
    description: 'Overview of your third project and its technical challenges.',
    technologies: ['TypeScript', 'AWS', 'Docker'],
    link: '#'
  }
])
</script>

<style scoped>
.portfolio-container {
  min-height: 100vh;
}

.hero-section {
  background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
}

.section-title {
  position: relative;
  padding-bottom: 0.5rem;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 50px;
  height: 3px;
  background-color: var(--bs-primary);
}

.skills-list {
  list-style-type: none;
  padding-left: 0;
}

.skills-list li {
  margin-bottom: 0.5rem;
  padding-left: 1.5rem;
  position: relative;
}

.skills-list li::before {
  content: '▹';
  position: absolute;
  left: 0;
  color: var(--bs-primary);
}

.card {
  transition: transform 0.2s ease-in-out;
}

.card:hover {
  transform: translateY(-5px);
}
</style> 