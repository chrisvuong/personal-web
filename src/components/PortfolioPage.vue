<template>
  <div class="portfolio-container" ref="portfolioContainer">
    <header class="hero-section py-5">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-md-8">
            <h1 class="display-4 fw-bold mb-3">Hi, I'm <span class="text-primary">Thien Phuc Vuong</span></h1>
            <h2 class="h3 text-secondary mb-4">Software Engineer</h2>
            <p class="lead mb-4">
              I specialise in full-stack development, with a passion for creating intuitive user experiences. 
            </p>
            <div class="d-flex gap-3">
              <button @click="downloadCV" class="btn btn-primary" :class="{ 'pdf-hidden': isGeneratingPDF }" :disabled="isGeneratingPDF">
                <i v-if="!isGeneratingPDF" class="bi bi-download me-2"></i>
                <i v-else class="bi bi-arrow-clockwise me-2 spin"></i>
                {{ isGeneratingPDF ? 'Generating PDF...' : 'Download My CV' }}
              </button>
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
              I'm a Software Engineer at Pay Advantage, with a strong background in full-stack development and a passion for solving complex problems. Previously, I worked at RightCrowd as a Junior Software Engineer and hold a Bachelor of Computer Science from Griffith University, graduating with an excellent GPA of 6.2/7.0.
            </p>
            <p class="mb-4">
              My core strengths are in .NET, Vue, SQL, and API development, supported by hands-on experience with tools like C#, Rider, AI integrations, IIS, and Docker. I thrive in fast-changing environments where innovation moves quickly, and I enjoy breaking down complex challenges into practical, well-analysed solutions.
            </p>
            <p class="mb-4">
              I'm motivated by creating impactful, reliable technology—most recently helping develop a robust payment solution with the Pay Advantage team. I believe in honesty, responsibility, and collaborative problem-solving, valuing both technical precision and teamwork.
            </p>
            <p class="mb-4">
              Beyond work, I enjoy chess for its strategic thinking and fishing for the patience it teaches—both skills I bring into my professional life. My long-term goal is to grow into a Senior Lead Engineer role, guiding teams in building large-scale, high-quality technology projects.
            </p>
            <h3 class="h5 mb-3">Technical Skills</h3>
            <ul class="skills-list">
              <li>.NET Development (C#, ASP.NET)</li>
              <li>Frontend Development (Vue.js, JavaScript/TypeScript)</li>
              <li>Database Design & Management (SQL)</li>
              <li>API Development & Integration</li>
              <li>DevOps Tools (Docker, IIS)</li>
              <li>Development Tools (Rider, Visual Studio)</li>
              <li>AI Integrations</li>
            </ul>
          </div>
          <div class="col-md-6">
            <div class="card">
              <div class="card-body">
                <h3 class="h5 mb-3">Quick Facts</h3>
                <ul class="list-unstyled">
                  <li class="mb-2">📍 Location: Brisbane/ Gold Coast</li>
                  <li class="mb-2">🎓 Education: Bachelor of Computer Science, Griffith University</li>
                  <li class="mb-2">📊 GPA: 6.2/7.0</li>
                  <li class="mb-2">💼 Current Role: Software Engineer at Pay Advantage</li>
                  <li class="mb-2">🔧 Previous: Junior Software Engineer at RightCrowd</li>
                  <li class="mb-2">🌐 Languages: Vietnamese, English</li>
                  <li class="mb-2">🎯 Goal: Senior Lead Engineer</li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="experiences" class="py-5 bg-light">
      <div class="container">
        <h2 class="section-title mb-4">Work Experiences</h2>
        
        <!-- Experience Summary -->
        <div class="experience-summary mb-4">
          <div class="row">
            <div class="col-md-6">
              <div class="summary-card">
                <div class="summary-icon">
                  <i class="bi bi-briefcase"></i>
                </div>
                <div class="summary-content">
                  <h4 class="summary-title">Total Experience</h4>
                  <p class="summary-value">{{ totalYearsExperience }} years</p>
                  <p class="summary-subtitle">Professional Software Development</p>
                </div>
              </div>
            </div>
            <div class="col-md-6">
              <div class="summary-card">
                <div class="summary-icon">
                  <i class="bi bi-calendar-check"></i>
                </div>
                <div class="summary-content">
                  <h4 class="summary-title">Current Role</h4>
                  <p class="summary-value">{{ currentRoleDuration }}</p>
                  <p class="summary-subtitle">{{ workExperiences[0].company }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
        
        <div class="experiences-timeline">
          <div class="experience-item" v-for="experience in workExperiences" :key="experience.id">
            <div class="experience-timeline-marker"></div>
            <div class="experience-content">
              <div class="experience-header">
                <h3 class="experience-title">{{ experience.title }}</h3>
                <div class="experience-company">
                  <i class="bi bi-building me-2"></i>
                  <a :href="experience.companyUrl" target="_blank" class="company-link">{{ experience.company }}</a>
                </div>
                <div class="experience-period">
                  <i class="bi bi-calendar3 me-2"></i>
                  {{ experience.startDate }} - {{ experience.endDate }}
                </div>
                <div class="experience-location">
                  <i class="bi bi-geo-alt me-2"></i>
                  {{ experience.location }}
                </div>
              </div>
              <div class="experience-description">
                <p>{{ experience.description }}</p>
                <div class="experience-achievements" v-if="experience.achievements">
                  <h4 class="achievements-title">Key Achievements:</h4>
                  <ul class="achievements-list">
                    <li v-for="achievement in experience.achievements" :key="achievement">{{ achievement }}</li>
                  </ul>
                </div>
                <div class="experience-technologies">
                  <h4 class="technologies-title">Technologies & Tools:</h4>
                  <div class="tech-badges">
                    <span v-for="tech in experience.technologies" :key="tech" 
                          class="badge bg-primary me-2 mb-2">{{ tech }}</span>
                  </div>
                </div>
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
                  <a href="callto:0426817316" class="text-dark" target="_blank">
                    <i class="bi bi-telephone fs-3"></i>
                  </a>
                  <a href="https://www.linkedin.com/in/thien-phuc-vuong/" class="text-dark" target="_blank">
                    <i class="bi bi-linkedin fs-3"></i>
                  </a>
                  <a href="mailto:chrisvuong20@gmail.com" class="text-dark">
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
import { ref, computed } from 'vue'
import html2pdf from 'html2pdf.js'

const workExperiences = ref([
  {
    id: 1,
    title: 'Software Engineer',
    company: 'Pay Advantage',
    companyUrl: 'https://www.payadvantage.com.au/',
    startDate: 'Novemver 2022',
    endDate: 'Present',
    location: 'Gold Coast, QLD',
    description: 'Working as a full-stack developer on payment solutions, focusing on creating robust and scalable applications that handle financial transactions securely.',
    achievements: [
      'Developed and maintained payment processing systems using .NET Framework and ASP.NET Core',
      'Implemented responsive frontend interfaces using Vue.js and modern JavaScript',
      'Collaborated with cross-functional teams to deliver high-quality software solutions',
      'Contributed to system architecture improvements and performance optimizations'
    ],
    technologies: ['Vue.js', '.NET Framework', 'ASP.NET Core', 'SQL Server', 'Docker', 'IIS', 'Rider', 'Visual Studio', 'C#', 'JavaScript']
  },
  {
    id: 2,
    title: 'Junior Software Engineer',
    company: 'RightCrowd',
    companyUrl: 'https://www.rightcrowd.com/',
    startDate: 'November 2021',
    endDate: 'October 2022',
    location: 'Gold Coast, QLD',
    description: 'Gained hands-on experience in software development while working on enterprise-level applications and learning industry best practices.',
    achievements: [
      'Assisted in developing and maintaining web applications using React and Node.js',
      'Participated in code reviews and contributed to team development processes',
      'Learned database management and API development practices',
      'Gained experience with agile development methodologies'
    ],
    technologies: ['React', 'Node.js', 'ArangoDB', 'JavaScript', 'HTML', 'CSS', 'Git']
  }
])

// Computed properties for experience calculations
const totalYearsExperience = computed(() => {
  const startDate = new Date('2021-11-01') // RightCrowd start date
  const endDate = new Date()
  const diffTime = Math.abs(endDate - startDate)
  const diffYears = diffTime / (1000 * 60 * 60 * 24 * 365.25)
  return Math.round(diffYears * 10) / 10 // Round to 1 decimal place
})

const currentRoleDuration = computed(() => {
  const startDate = new Date('2022-11-01') // Pay Advantage start date
  const endDate = new Date()
  const diffTime = Math.abs(endDate - startDate)
  const diffYears = diffTime / (1000 * 60 * 60 * 24 * 365.25)
  const years = Math.floor(diffYears)
  const months = Math.floor((diffYears - years) * 12)
  
  if (years === 0) {
    return `${months} months`
  } else if (months === 0) {
    return `${years} year${years > 1 ? 's' : ''}`
  } else {
    return `${years} year${years > 1 ? 's' : ''} ${months} month${months > 1 ? 's' : ''}`
  }
})

const portfolioContainer = ref(null)
const isGeneratingPDF = ref(false)

const downloadCV = async () => {
  try {
    if (!portfolioContainer.value) {
      alert('Portfolio container not found. Please ensure the ref is correct.')
      return
    }

    isGeneratingPDF.value = true

    // Configure PDF options
    const opt = {
      margin: [10, 10, 10, 10],
      filename: 'Thien_Phuc_Vuong_CV.pdf',
      image: { type: 'jpeg', quality: 0.98 },
      html2canvas: { scale: 2, useCORS: true },
      jsPDF: { unit: 'mm', format: 'a4', orientation: 'portrait' }
    }
    
    // Generate and download PDF
    await html2pdf().from(portfolioContainer.value).set(opt).save()
    
  } catch (error) {
    console.error('Error generating PDF:', error)
    alert('There was an error generating your CV. Please try again.')
  } finally {
    isGeneratingPDF.value = false
  }
}
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

.pdf-hidden {
  display: none;
}

.spin {
  animation: spin 1s linear infinite;
}

@keyframes spin {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

/* Experience Summary Styles */
.experience-summary {
  margin-bottom: 2rem;
}

.summary-card {
  background: white;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  border: 1px solid #e9ecef;
  height: 100%;
  display: flex;
  align-items: center;
  gap: 1rem;
}

.summary-icon {
  background: var(--bs-primary);
  color: white;
  width: 3rem;
  height: 3rem;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.25rem;
  flex-shrink: 0;
}

.summary-content {
  flex: 1;
}

.summary-title {
  font-size: 0.9rem;
  font-weight: 600;
  color: #6c757d;
  margin-bottom: 0.5rem;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.summary-value {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--bs-primary);
  margin-bottom: 0.25rem;
}

.summary-subtitle {
  font-size: 0.85rem;
  color: #6c757d;
  margin-bottom: 0;
}

/* Work Experience Tree Styles */
.experiences-timeline {
  position: relative;
  padding-left: 1.5rem;
}

.experiences-timeline::before {
  content: '';
  position: absolute;
  left: 0.75rem;
  top: 0;
  bottom: 0;
  width: 1px;
  background: #dee2e6;
}

.experience-item {
  position: relative;
  margin-bottom: 2rem;
}

.experience-timeline-marker {
  position: absolute;
  left: -1.25rem;
  top: 0.25rem;
  width: 0.5rem;
  height: 0.5rem;
  background: var(--bs-primary);
  border-radius: 50%;
}

.experience-content {
  background: transparent;
  padding: 0;
  border: none;
  box-shadow: none;
}

.experience-content:hover {
  transform: none;
  box-shadow: none;
}

.experience-header {
  margin-bottom: 0.75rem;
}

.experience-title {
  color: var(--bs-primary);
  font-weight: 600;
  margin-bottom: 0.25rem;
  font-size: 1.1rem;
}

.experience-company,
.experience-period,
.experience-location {
  display: flex;
  align-items: center;
  margin-bottom: 0.25rem;
  color: #6c757d;
  font-size: 0.9rem;
}

.company-link {
  color: var(--bs-primary);
  text-decoration: none;
  font-weight: 500;
}

.company-link:hover {
  text-decoration: underline;
}

.experience-description {
  color: #495057;
  line-height: 1.5;
  margin-left: 1rem;
}

.experience-description p {
  margin-bottom: 0.75rem;
}

.achievements-title,
.technologies-title {
  font-size: 0.9rem;
  font-weight: 600;
  color: #495057;
  margin-bottom: 0.5rem;
  margin-top: 1rem;
}

.achievements-list {
  list-style-type: none;
  padding-left: 0;
  margin-bottom: 1rem;
}

.achievements-list li {
  margin-bottom: 0.25rem;
  padding-left: 1rem;
  position: relative;
  color: #495057;
  font-size: 0.9rem;
}

.achievements-list li::before {
  content: '•';
  position: absolute;
  left: 0;
  color: var(--bs-primary);
}

.tech-badges {
  display: flex;
  flex-wrap: wrap;
  gap: 0.25rem;
}

.tech-badges .badge {
  font-size: 0.75rem;
  padding: 0.25rem 0.5rem;
  background: #f8f9fa !important;
  color: #495057 !important;
  border: 1px solid #dee2e6;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .experiences-timeline {
    padding-left: 1rem;
  }
  
  .experiences-timeline::before {
    left: 0.5rem;
  }
  
  .experience-timeline-marker {
    left: -0.75rem;
  }
  
  .experience-description {
    margin-left: 0.5rem;
  }
  
  .summary-card {
    padding: 1rem;
    margin-bottom: 1rem;
  }
  
  .summary-icon {
    width: 2.5rem;
    height: 2.5rem;
    font-size: 1rem;
  }
  
  .summary-value {
    font-size: 1.25rem;
  }
}

/* PDF/Print optimization */
@media print {
  .portfolio-container {
    padding: 0;
    margin: 0;
  }
  
  .hero-section {
    background: none !important;
    padding: 20px 0 !important;
  }
  
  .card {
    box-shadow: none !important;
    border: 1px solid #ddd !important;
  }
  
  .summary-card {
    box-shadow: none !important;
    border: 1px solid #ddd !important;
  }
  
  .btn {
    display: none !important;
  }
  
  .experiences-timeline::before {
    display: none;
  }
  
  .experience-timeline-marker {
    display: none;
  }
  
  .experience-content {
    margin-bottom: 1rem;
  }
  
  .experience-description {
    margin-left: 0 !important;
  }
}
</style> 