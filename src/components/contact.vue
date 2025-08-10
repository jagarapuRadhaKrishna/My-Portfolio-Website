<template>
  <div>
    <footer class="mt-2 text-lg-start modern-footer" id="contact">
      <hr class="my-2"/>
        <section class="row">
            <div class="col-md-3 col-lg-3 col-xl-3 mx-auto mt-2">
              <h6 class="text-uppercase mb-4 font-weight-bold contact-title">Contact Details</h6>
              <p class="contact-item">
                <a href="https://www.linkedin.com/in/jagarapuradhakrishna" target="_blank" class="contact-link">
                  <i class="fab fa-linkedin"></i> LinkedIn
                </a>
              </p>
              <p class="contact-item">
                <a href="https://github.com/jagarapuRadhaKrishna" target="_blank" class="contact-link">
                  <i class="fab fa-github"></i> GitHub
                </a>
              </p>
              <p class="contact-item">
                <a href="https://leetcode.com/u/Radhakrishna02256/" target="_blank" class="contact-link">
                  <i class="fas fa-code"></i> LeetCode
                </a>
              </p>
              <p class="contact-item">
                <a href="mailto:radhakrishna02256@gmail.com" class="contact-link">
                  <i class="fas fa-envelope"></i> radhakrishna02256@gmail.com
                </a>
              </p>
              <p class="contact-item location">
                <i class="fas fa-map-marker-alt"></i> India
              </p>
            </div>

            <div class="col-md-2 col-lg-2 col-xl-2 mx-auto mt-2">
              <h6 class="text-uppercase mb-4 font-weight-bold contact-title">Services</h6>
              <p class="service-item">Full Stack Development</p>
              <p class="service-item">Backend Development</p>
              <p class="service-item">AI/ML Solutions</p>
              <p class="service-item">REST API Development</p>
            </div>

            <div class="col-md-4 col-lg-3 col-xl-3 mx-auto mt-2">
              <h6 class="text-uppercase mb-4 font-weight-bold contact-title">Navigation</h6>
              <p class="scroll-to nav-link" @click="scrollToSection('summary')">Home</p>
              <p class="scroll-to nav-link" @click="scrollToSection('about')">About</p>
              <p class="scroll-to nav-link" @click="scrollToSection('practicle_skills')">Skills</p>
              <p class="scroll-to nav-link" @click="scrollToSection('projects')">Projects</p>
            </div>

            <div class="col-md-3 col-lg-2 col-xl-2 mx-auto mt-2">
              <h6 class="text-uppercase mb-4 font-weight-bold contact-title">Connect With Me</h6>
              <div class="social-buttons">
                <a class="social-btn linkedin-btn" href="https://www.linkedin.com/in/jagarapuradhakrishna" target="_blank" role="button">
                  <i class="fab fa-linkedin-in"></i>
                </a>
                <a class="social-btn github-btn" href="https://github.com/jagarapuRadhaKrishna" target="_blank" role="button">
                  <i class="fab fa-github"></i>
                </a>
                <a class="social-btn leetcode-btn" href="https://leetcode.com/u/Radhakrishna02256/" target="_blank" role="button">
                  <i class="fas fa-code"></i>
                </a>
                <a class="social-btn gmail-btn" href="mailto:radhakrishna02256@gmail.com" role="button">
                  <i class="fas fa-envelope"></i>
                </a>
              </div>
            </div>
        </section>
      <hr class="footer-divider"/>
      <div class="text-center p-3 footer-bottom">
        © 2025 Radha Krishna Portfolio | Made with 
        <a href="https://github.com/jagarapuRadhaKrishna/Portfolio" class="portfolio-link">Vue.js</a>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: "FooterComponent",
  methods: {
     scrollToSection(sectionId) {
      const element = document.getElementById(sectionId);
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' });
      }
    }
  }
};
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Rajdhani:wght@300;400;500;600;700&display=swap');

/* Contact section container */
#contact {
  scroll-snap-align: start;
  scroll-behavior: smooth;
  width: 100%;
  display: block;
}

.modern-footer {
  background: linear-gradient(135deg, #0f0f23 0%, #1a1a2e 50%, #16213e 100%);
  color: #e0e6ed;
  font-family: 'Rajdhani', sans-serif;
  position: relative;
  padding: 40px 20px;
  margin: 0;
  width: 100%;
  scroll-snap-align: start;
  scroll-behavior: smooth;
  
  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: 
      radial-gradient(circle at 20% 80%, rgba(120, 119, 198, 0.1) 0%, transparent 50%),
      radial-gradient(circle at 80% 20%, rgba(255, 119, 198, 0.1) 0%, transparent 50%);
    pointer-events: none;
  }
  
  section.row {
    position: relative;
    z-index: 2;
  }
}

.contact-title {
  color: #64ffda;
  font-weight: 600;
  font-size: 1rem; /* Standardized font size */
  text-shadow: 0 2px 4px rgba(100, 255, 218, 0.3);
  margin-bottom: 1rem !important; /* Reduced gap */
}

.contact-item,
.service-item,
.nav-link {
  margin-bottom: 0.5rem; /* Reduced gap between items */
  transition: all 0.3s ease;
  font-size: 1rem;
  font-weight: 400;
}

.contact-link {
  color: #e0e6ed;
  text-decoration: none;
  display: flex;
  align-items: center;
  gap: 10px;
  transition: all 0.3s ease;
  padding: 8px 0;
  
  i {
    width: 20px;
    color: #64ffda;
    font-size: 1.1rem;
  }
  
  &:hover {
    color: #64ffda;
    text-decoration: none;
    transform: translateX(5px);
    text-shadow: 0 2px 4px rgba(100, 255, 218, 0.3);
  }
}

.service-item {
  color: #e0e6ed;
  padding: 5px 0;
  border-left: 3px solid transparent;
  padding-left: 15px;
  transition: all 0.3s ease;
  
  &:hover {
    border-left-color: #ff6b6b;
    color: #fff;
    transform: translateX(5px);
  }
}

.scroll-to.nav-link {
  cursor: pointer;
  color: #e0e6ed;
  padding: 8px 0;
  border-bottom: 1px solid transparent;
  transition: all 0.3s ease;
  
  &:hover {
    color: #64ffda;
    border-bottom-color: #64ffda;
    transform: translateX(5px);
  }
}

.location {
  color: #e0e6ed;
  
  i {
    color: #ff6b6b;
    margin-right: 10px;
  }
}

.social-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.social-btn {
  width: 45px;
  height: 45px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  transition: all 0.3s ease;
  border: 2px solid rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(10px);
  position: relative;
  overflow: hidden;
  
  i {
    font-size: 1.2rem;
    color: #fff;
    transition: all 0.3s ease;
    z-index: 2;
    position: relative;
  }
  
  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    opacity: 0;
    transition: all 0.3s ease;
    z-index: 1;
  }
  
  &:hover {
    transform: translateY(-3px) scale(1.1);
    text-decoration: none;
    
    &::before {
      opacity: 1;
    }
  }
}

.linkedin-btn {
  &::before {
    background: linear-gradient(45deg, #0077b5, #00a0dc);
  }
  
  &:hover {
    box-shadow: 0 8px 20px rgba(0, 119, 181, 0.4);
  }
}

.github-btn {
  &::before {
    background: linear-gradient(45deg, #333, #555);
  }
  
  &:hover {
    box-shadow: 0 8px 20px rgba(51, 51, 51, 0.4);
  }
}

.leetcode-btn {
  &::before {
    background: linear-gradient(45deg, #ffa116, #f89b2f);
  }
  
  &:hover {
    box-shadow: 0 8px 20px rgba(255, 161, 22, 0.4);
  }
}

.gmail-btn {
  &::before {
    background: linear-gradient(45deg, #ea4335, #d93025);
  }
  
  &:hover {
    box-shadow: 0 8px 20px rgba(234, 67, 53, 0.4);
  }
}

.footer-divider {
  border-color: rgba(100, 255, 218, 0.3);
  margin: 2rem 0 1rem 0;
}

.footer-bottom {
  color: #a0a0a0;
  font-size: 0.9rem;
  
  .portfolio-link {
    color: #64ffda;
    text-decoration: none;
    font-weight: 600;
    transition: all 0.3s ease;
    
    &:hover {
      color: #fff;
      text-shadow: 0 2px 4px rgba(100, 255, 218, 0.3);
    }
  }
}

/* Responsive Design */
@media screen and (max-width: 768px) {
  .social-buttons {
    justify-content: center;
  }
  
  .contact-item,
  .service-item,
  .nav-link {
    text-align: center;
  }
  
  .contact-link {
    justify-content: center;
  }
}

@media screen and (max-width: 480px) {
  .social-btn {
    width: 40px;
    height: 40px;
    
    i {
      font-size: 1rem;
    }
  }
  
  .contact-title {
    font-size: 1rem;
    text-align: center;
  }
}
</style>
