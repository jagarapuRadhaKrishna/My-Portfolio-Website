<template>
  <section id="projects">
    <Heading :title="'My Projects'" :subtitle="'Have a look at'" />

    <section class="project-container container-fluid">
      <div class="card px-0">
        <img src="/projects/nxt_hire_new.png" class="card-img-top" alt="NXT-Hire Project"/>

        <div class="card-body shadow">
            <h5 class="card-title-small">NXT-Hire</h5>
            <p class="card-text">
              An intelligent career coaching platform that leverages AI and machine learning to provide personalized career guidance, 
              resume optimization, and job matching.
            </p>
            <div class="d-flex">
                <a href="https://github.com/jagarapuRadhaKrishna/NXT-Hire-" target="_blank" class="btn me-2">
                  <i class="fa-brands fa-github mr-2"></i>GitHub
                </a>
                <a href="https://hirewith-nxthire.netlify.app/" target="_blank" class="btn me-2">
                  <i class="fa-solid fa-arrow-up-right-from-square"></i> Live Demo
                </a>
                <button @click="openProjectModal" class="btn">
                  <i class="fa-solid fa-info-circle"></i> Details
                </button>
            </div>
        </div>
      </div>
    </section>

    <!-- Project Details Modal -->
    <transition name="modal-fade">
      <div v-if="showModal" class="project-modal-wrapper">
        <div class="project-modal-overlay" @click="closeProjectModal">
          <div class="project-modal-content" @click.stop>
            <button class="modal-close-btn" @click="closeProjectModal">
              <i class="fa-solid fa-times"></i>
            </button>
            
            <div class="modal-header">
              <h2 class="project-modal-title">NXT-Hire - AI-Powered Career Platform</h2>
            </div>
            
            <div class="modal-body">
          <div class="project-links mb-4">
            <a href="https://github.com/jagarapuRadhaKrishna/NXT-Hire-" target="_blank" class="modal-btn me-3">
              <i class="fa-brands fa-github mr-2"></i>GitHub Repository
            </a>
            <a href="https://hirewith-nxthire.netlify.app/" target="_blank" class="modal-btn">
              <i class="fa-solid fa-arrow-up-right-from-square mr-2"></i>Live Demo
            </a>
          </div>

          <div class="project-section">
            <h3>Project Overview</h3>
            <p>An intelligent career coaching platform that leverages AI and machine learning to provide personalized career guidance, resume optimization, and job matching. Features include NLP-based resume parsing, real-time analytics, and an interactive dashboard for career development.</p>
          </div>

          <div class="project-section">
            <h3>✨ Features</h3>
            <ul class="features-list">
              <li>🧠 <strong>AI Resume Analyzer (OpenAI/Gemini)</strong> - Intelligent resume parsing and optimization suggestions</li>
              <li>💼 <strong>Smart Job Portal with match scoring</strong> - AI-powered job recommendations</li>
              <li>📑 <strong>Cover Letter Generator</strong> - Personalized cover letters using AI</li>
              <li>🔐 <strong>Clerk Authentication (User/Employer roles)</strong> - Secure multi-role authentication</li>
              <li>🧭 <strong>Career Roadmap Generator</strong> - AI-generated personalized career paths</li>
              <li>📊 <strong>Application Tracker Dashboard</strong> - Track job applications and progress</li>
              <li>🎯 <strong>Interview Preparation</strong> - Mock interviews and practice questions</li>
              <li>🎨 <strong>Fully Responsive UI (Tailwind CSS + shadcn/ui components)</strong></li>
              <li>🌑 <strong>Dark Mode Support</strong> - Complete theme switching capability</li>
            </ul>
          </div>

          <div class="project-section">
            <h3>🛠️ Tech Stack</h3>
            <div class="tech-category">
              <h4>Frontend:</h4>
              <p>React 18, Next.js 15 (App Router), TypeScript</p>
            </div>
            <div class="tech-category">
              <h4>Styling:</h4>
              <p>Tailwind CSS, shadcn/ui, Framer Motion</p>
            </div>
            <div class="tech-category">
              <h4>Backend:</h4>
              <p>Next.js API routes, Prisma ORM</p>
            </div>
            <div class="tech-category">
              <h4>Database:</h4>
              <p>PostgreSQL (Neon DB)</p>
            </div>
            <div class="tech-category">
              <h4>AI/ML:</h4>
              <p>OpenAI GPT-4, Google Gemini APIs</p>
            </div>
          </div>
            </div>
          </div>
        </div>
      </div>
    </transition>
  </section>
</template>

<script>
  import Heading from "./common/heading.vue";
 
  export default {
    name: 'MyComponent',
    components: { Heading },
    data() {
      return {
        showModal: false
      }
    },
    beforeDestroy() {
      // Ensure scrolling is restored if component is destroyed
      document.body.style.overflow = '';
    },
    methods: {
      viewUrl(url) {
        window.location.href = url;
      },
      openProjectModal() {
        this.showModal = true;
        document.body.style.overflow = 'hidden';
        document.documentElement.style.overflow = 'hidden';
        document.body.style.position = 'fixed';
        document.body.style.width = '100%';
      },
      closeProjectModal() {
        this.showModal = false;
        document.body.style.overflow = '';
        document.documentElement.style.overflow = '';
        document.body.style.position = '';
        document.body.style.width = '';
      }
    }
  }
</script>

<style scoped lang="scss">
/* Projects section styling for black grid design */
.project-container {
  gap: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start; /* Left align instead of center */
  padding-left: 48px; /* Half inch from left edge */
  margin-top: 0; /* Remove any top margin */
  padding-top: 0; /* Remove any top padding */
  
  .card {
    width: 28rem; /* Reduced from 35rem */
    transition: all 0.3s ease-in-out;
    background: rgba(255, 255, 255, 0.05) !important;
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.2) !important;
    border-radius: 15px;
    overflow: hidden;

    &:hover {
      transform: scale(1.05) translateY(-10px);
      z-index: 2;
      background: rgba(255, 255, 255, 0.1) !important;
      box-shadow: 0 20px 40px rgba(255, 255, 255, 0.1);
      border-color: rgba(255, 255, 255, 0.4) !important;
    }

    .card-img-top {
      transition: all 0.3s ease;
      filter: brightness(0.9);
    }

    &:hover .card-img-top {
      filter: brightness(1.1);
      transform: scale(1.02);
    }

    .card-body {
      background: transparent !important;
      color: white !important;
      
      .card-title {
        color: white !important;
        font-weight: bold;
        text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
        font-size: 1.5rem;
      }
      
      .card-title-small {
        color: white !important;
        font-weight: bold;
        text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
        font-size: 1rem; /* Standardized font size */
        text-align: left; /* Left aligned */
        margin-bottom: 0.5rem;
      }
      
      .card-text {
        color: rgba(255, 255, 255, 0.9) !important;
        text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.8);
        font-size: 1rem; /* Standardized font size */
      }
      
      .btn {
        background: rgba(255, 255, 255, 0.1) !important;
        border: 1px solid rgba(255, 255, 255, 0.3) !important;
        color: white !important;
        text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.8);
        transition: all 0.3s ease;
        
        &:hover {
          background: rgba(255, 255, 255, 0.2) !important;
          transform: translateY(-2px);
          box-shadow: 0 5px 15px rgba(255, 255, 255, 0.2);
          text-decoration: underline;
        }
      }
    }
    
    a:hover {
      text-decoration: underline;
    }
  }
}

/* Project Modal Styles */
.project-modal-wrapper {
  position: fixed !important;
  top: 0 !important;
  left: 0 !important;
  right: 0 !important;
  bottom: 0 !important;
  width: 100vw !important;
  height: 100vh !important;
  z-index: 99999999 !important;
  background: #000000 !important;
}

.project-modal-overlay {
  position: fixed !important;
  top: 0 !important;
  left: 0 !important;
  right: 0 !important;
  bottom: 0 !important;
  width: 100% !important;
  height: 100% !important;
  background: #000000 !important;
  backdrop-filter: none !important;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  z-index: 99999999 !important;
  padding: 80px 20px 60px 20px;
  overflow-y: auto;
  overflow-x: hidden;
}

.project-modal-content {
  background: rgba(10, 10, 10, 0.99);
  border: 1px solid rgba(255, 255, 255, 0.3);
  border-radius: 20px;
  max-width: 700px;
  width: 90%;
  position: relative;
  backdrop-filter: blur(20px);
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.8);
  margin: 0 auto 60px auto;
  z-index: 1000000;
  pointer-events: auto;
}

.modal-fade-enter-active, .modal-fade-leave-active {
  transition: opacity 0.3s ease;
}

.modal-fade-enter, .modal-fade-leave-to {
  opacity: 0;
}

.modal-close-btn {
  position: absolute;
  top: 20px;
  right: 25px;
  background: rgba(0, 0, 0, 0.8);
  border: 2px solid white;
  color: white;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 18px;
  z-index: 10000;
  transition: all 0.3s ease;

  &:hover {
    background: rgba(255, 255, 255, 0.2);
    transform: scale(1.1);
  }
}

.modal-header {
  padding: 20px 30px 15px 30px; /* Reduced padding */
  border-bottom: 1px solid rgba(255, 255, 255, 0.2); /* More visible border */
  background: rgba(0, 0, 0, 0.3); /* Slight background for separation */
}

.project-modal-title {
  color: white;
  margin: 0;
  font-size: 1.6rem; /* Reduced from 2rem */
  font-weight: bold;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
}

.modal-body {
  padding: 20px 30px; /* Reduced padding */
  color: white;
}

.project-links {
  display: flex;
  gap: 15px;
  margin-bottom: 30px;
}

.modal-btn {
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.3);
  color: white;
  padding: 12px 24px;
  border-radius: 10px;
  text-decoration: none;
  transition: all 0.3s ease;
  display: inline-flex;
  align-items: center;
  
  &:hover {
    background: rgba(255, 255, 255, 0.2);
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(255, 255, 255, 0.2);
    color: white;
    text-decoration: none;
  }
}

.project-section {
  margin-bottom: 30px;
  
  h3 {
    color: #64ffda; /* Brighter color for better visibility */
    font-size: 1.4rem;
    margin-bottom: 15px;
    font-weight: 600;
  }
  
  p {
    color: rgba(255, 255, 255, 0.95); /* Higher opacity for better readability */
    line-height: 1.6;
    margin-bottom: 15px;
  }
}

.features-list {
  list-style: none;
  padding: 0;
  
  li {
    color: rgba(255, 255, 255, 0.95); /* Better visibility */
    margin-bottom: 12px;
    line-height: 1.5;
    padding-left: 0;
    
    strong {
      color: white;
    }
  }
}

.tech-category {
  margin-bottom: 15px;
  
  h4 {
    color: #64ffda; /* Consistent with other headings */
    font-size: 1.1rem;
    margin-bottom: 5px;
    font-weight: 600;
  }
  
  p {
    margin-bottom: 10px;
    padding-left: 15px;
    color: rgba(255, 255, 255, 0.95); /* Better visibility */
  }
}

/* Responsive */
@media (max-width: 768px) {
  .project-container {
    padding-left: 20px; /* Reduced padding on mobile */
    justify-content: center; /* Center on mobile for better fit */
  }
  
  .project-modal-content {
    margin: 10px;
    max-height: 85vh; /* Reduced on mobile */
    max-width: 95%; /* Almost full width on mobile */
    width: 95%;
  }
  
  .modal-header,
  .modal-body {
    padding: 15px; /* Further reduced padding on mobile */
  }
  
  .project-modal-title {
    font-size: 1.3rem; /* Reduced title size on mobile */
  }
  
  .project-links {
    flex-direction: column;
  }
}
</style>
