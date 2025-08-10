<template>
  <section id="projects">
    <Heading :title="'My Projects'" :subtitle="'Have a look at'" />

    <section class="project-container container-fluid">
      <div class="card px-0">
        <img src="/projects/nxt_hire_project.png" class="card-img-top" alt="NXT-Hire Project"/>

        <div class="card-body shadow">
            <h5 class="card-title">NXT-Hire - AI-Powered Career Platform</h5>
            <p class="card-text">
              An intelligent career coaching platform that leverages AI and machine learning to provide personalized career guidance, 
              resume optimization, and job matching. Features include NLP-based resume parsing, real-time analytics, 
              and an interactive dashboard for career development.
            </p>
            <div class="mb-3">
              <span class="badge rounded-pill px-3 py-2 mx-2 border border-dark">Java Spring Boot</span>
              <span class="badge rounded-pill px-3 py-2 mx-2 border border-dark">Node.js</span>
              <span class="badge rounded-pill px-3 py-2 mx-2 border border-dark">Next.js</span>
              <span class="badge rounded-pill px-3 py-2 mx-2 border border-dark">AI/ML</span>
              <span class="badge rounded-pill px-3 py-2 mx-2 border border-dark">PostgreSQL</span>
              <span class="badge rounded-pill px-3 py-2 mx-2 border border-dark">NLP</span>
            </div>
            <div class="d-flex">
                <a href="https://github.com/jagarapuRadhaKrishna/NXT-Hire-" target="_blank" class="btn me-2">
                  <i class="fa-brands fa-github mr-2"></i>GitHub
                </a>
                <a href="https://hirewith-nxthire.netlify.app/" target="_blank" class="btn">
                  <i class="fa-solid fa-arrow-up-right-from-square"></i>  Live Demo
                </a>
            </div>
        </div>
      </div>
    </section>
  </section>
</template>

<script>
  import Heading from "./common/heading.vue";
 
  export default {
    name: 'MyComponent',
    components: { Heading },
    methods: {
      viewUrl(url) {
        window.location.href = url;
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
  justify-content: center;
  
  .card {
    width: 30rem;
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
      }
      
      .card-text {
        color: rgba(255, 255, 255, 0.9) !important;
        text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.8);
      }
      
      .badge {
        background: rgba(255, 255, 255, 0.1) !important;
        border: 1px solid rgba(255, 255, 255, 0.3) !important;
        color: white !important;
        transition: all 0.3s ease;
        
        &:hover {
          background: rgba(255, 255, 255, 0.2) !important;
          transform: scale(1.05);
        }
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
</style>
