<template>
  <section id="summary" class="section section_1 py-5 w-100 modern-hero">
    <div class="animated-background">
      <div class="gradient-orb orb-1"></div>
      <div class="gradient-orb orb-2"></div>
      <div class="gradient-orb orb-3"></div>
    </div>

    <div class="container-fluid">
      <div class="row min-vh-100 align-items-center">
        <div data-aos="zoom-in" data-aos-duration="1200" class="col-12 px-4 py-5 d-flex justify-content-center align-items-center flex-column hero-content">
          
          <div class="hero-badge mb-4">
            <span class="status-dot"></span>
            <span class="badge-text">Available for Opportunities</span>
          </div>

          <div class="main-title">
            <h1 class="name-title">
              <span class="hello-text">Hello, I'm</span>
              <span class="name-highlight">Radha Krishna</span>
            </h1>
          </div>
          
          <div class="role-container">
            <h2 class="role-text">
              <span class="role-label">Full Stack Engineer</span>
              <span class="role-separator">•</span>
              <span class="role-label">AI Enthusiast</span>
            </h2>
          </div>

          <p class="intro-para mt-4"> 
            Crafting high-performance, scalable applications with expertise in 
            <span class="tech-highlight">Java Spring Boot</span>, 
            <span class="tech-highlight">Node.js</span>, 
            <span class="tech-highlight">React</span>, and 
            <span class="tech-highlight">Next.js</span>. 
            Building AI-powered solutions and delivering real-world impact through elegant, user-focused software.
          </p>

          <div class="stats-container">
            <div class="stat-item" data-aos="fade-up" data-aos-delay="100">
              <div class="stat-value">10+</div>
              <div class="stat-label">Projects Delivered</div>
            </div>
            <div class="stat-item" data-aos="fade-up" data-aos-delay="200">
              <div class="stat-value">Top 10%</div>
              <div class="stat-label">LeetCode</div>
            </div>
            <div class="stat-item" data-aos="fade-up" data-aos-delay="300">
              <div class="stat-value">Full Stack</div>
              <div class="stat-label">Expertise</div>
            </div>
          </div>

          <div class="btn-container mt-5">
            <button
              class="btn btn-modern btn-primary"
              onclick="location.href='https://drive.google.com/file/d/1lmklnLJ3cSxYzAYWyqsZxZ0m-VClKhEd/view?usp=sharing'"
            >
              <i class="fas fa-file-pdf mr-2"></i>
              <span>Download Resume</span>
              <div class="btn-shine"></div>
            </button>
            <button class="btn btn-modern btn-secondary" @click="scrollToSection('contact')">
              <i class="fas fa-paper-plane mr-2"></i>
              <span>Let's Connect</span>
              <div class="btn-shine"></div>
            </button>
          </div>

          <div class="social-links-modern mt-5">
            <a href="https://www.linkedin.com/in/jagarapuradhakrishna" target="_blank" class="social-icon linkedin" data-aos="zoom-in" data-aos-delay="100">
              <i class="fab fa-linkedin-in"></i>
              <span class="tooltip">LinkedIn</span>
            </a>
            <a href="https://github.com/jagarapuRadhaKrishna" target="_blank" class="social-icon github" data-aos="zoom-in" data-aos-delay="200">
              <i class="fab fa-github"></i>
              <span class="tooltip">GitHub</span>
            </a>
            <a href="https://leetcode.com/u/Radhakrishna02256/" target="_blank" class="social-icon leetcode" data-aos="zoom-in" data-aos-delay="300">
              <i class="fas fa-code"></i>
              <span class="tooltip">LeetCode</span>
            </a>
            <a href="mailto:radhakrishna02256@gmail.com" class="social-icon gmail" data-aos="zoom-in" data-aos-delay="400">
              <i class="fas fa-envelope"></i>
              <span class="tooltip">Email</span>
            </a>
          </div>

          <div class="scroll-indicator">
            <div class="mouse">
              <div class="wheel"></div>
            </div>
            <p>Scroll to explore</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import html2pdf from 'html2pdf.js';

export default {
  methods: {
    redirectTo(url) {
      window.location.href = url;
    },
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

.modern-hero {
  background: transparent;
  min-height: 100vh;
  position: relative;
  overflow: hidden;
  display: flex;
  align-items: center;
  padding-top: 80px;
}

.animated-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
  z-index: 0;
}

.gradient-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  opacity: 0.6;
  animation: float 20s ease-in-out infinite;
}

.orb-1 {
  width: 500px;
  height: 500px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  top: -100px;
  left: -100px;
  animation-delay: 0s;
}

.orb-2 {
  width: 400px;
  height: 400px;
  background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
  bottom: -100px;
  right: -100px;
  animation-delay: -5s;
}

.orb-3 {
  width: 450px;
  height: 450px;
  background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  animation-delay: -10s;
}

@keyframes float {
  0%, 100% {
    transform: translate(0, 0) scale(1);
  }
  33% {
    transform: translate(30px, -30px) scale(1.1);
  }
  66% {
    transform: translate(-20px, 20px) scale(0.9);
  }
}

.hero-content {
  align-items: center !important;
  text-align: center !important;
  position: relative;
  z-index: 1;
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 10px 24px;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 50px;
  font-family: 'Inter', sans-serif;
  font-size: 0.9rem;
  font-weight: 500;
  color: #fff;
  animation: glow 2s ease-in-out infinite;
  
  .status-dot {
    width: 8px;
    height: 8px;
    background: #4ade80;
    border-radius: 50%;
    animation: pulse 2s ease-in-out infinite;
  }
}

@keyframes pulse {
  0%, 100% {
    box-shadow: 0 0 0 0 rgba(74, 222, 128, 0.7);
  }
  50% {
    box-shadow: 0 0 0 10px rgba(74, 222, 128, 0);
  }
}

@keyframes glow {
  0%, 100% {
    box-shadow: 0 0 20px rgba(255, 255, 255, 0.1);
  }
  50% {
    box-shadow: 0 0 30px rgba(255, 255, 255, 0.2);
  }
}

.main-title {
  margin-bottom: 1.5rem;
}

.name-title {
  font-family: 'Space Grotesk', sans-serif;
  font-weight: 700;
  text-align: center;
  margin: 0;
  
  .hello-text {
    display: block;
    font-size: 1.5rem;
    font-weight: 500;
    color: rgba(255, 255, 255, 0.7);
    margin-bottom: 0.5rem;
    letter-spacing: 2px;
  }
  
  .name-highlight {
    display: block;
    font-size: 4.5rem;
    font-weight: 800;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 50%, #f093fb 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    letter-spacing: -2px;
    line-height: 1.1;
    animation: gradientShift 5s ease infinite;
    background-size: 200% 200%;
  }
  
  @media (max-width: 768px) {
    .hello-text {
      font-size: 1.2rem;
    }
    .name-highlight {
      font-size: 3rem;
    }
  }
  
  @media (max-width: 480px) {
    .hello-text {
      font-size: 1rem;
    }
    .name-highlight {
      font-size: 2.5rem;
    }
  }
}

@keyframes gradientShift {
  0%, 100% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
}

.role-container {
  margin-bottom: 1rem;
}

.role-text {
  font-family: 'Inter', sans-serif;
  font-size: 1.5rem;
  font-weight: 600;
  color: rgba(255, 255, 255, 0.9);
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
  flex-wrap: wrap;
  
  .role-label {
    position: relative;
    
    &::after {
      content: '';
      position: absolute;
      bottom: -5px;
      left: 0;
      width: 100%;
      height: 2px;
      background: linear-gradient(90deg, transparent, #667eea, transparent);
    }
  }
  
  .role-separator {
    color: #667eea;
    font-size: 1.2rem;
  }
  
  @media (max-width: 768px) {
    font-size: 1.2rem;
  }
}

.intro-para {
  max-width: 700px;
  font-family: 'Inter', sans-serif;
  font-weight: 400;
  font-size: 1.1rem;
  line-height: 1.8;
  color: rgba(255, 255, 255, 0.8);
  text-align: center;
  margin: 0 auto;
  
  .tech-highlight {
    color: #667eea;
    font-weight: 600;
    position: relative;
    
    &::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 1px;
      background: linear-gradient(90deg, transparent, #667eea, transparent);
    }
  }
  
  @media (max-width: 768px) {
    font-size: 1rem;
  }
}

.stats-container {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 3rem;
  margin: 3rem 0;
  flex-wrap: wrap;
  
  .stat-item {
    text-align: center;
    padding: 1.5rem 2rem;
    background: rgba(255, 255, 255, 0.05);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 20px;
    transition: all 0.3s ease;
    
    &:hover {
      transform: translateY(-5px);
      background: rgba(255, 255, 255, 0.08);
      border-color: rgba(102, 126, 234, 0.5);
      box-shadow: 0 10px 30px rgba(102, 126, 234, 0.2);
    }
    
    .stat-value {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 2rem;
      font-weight: 700;
      color: #fff;
      margin-bottom: 0.5rem;
      background: linear-gradient(135deg, #667eea, #764ba2);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }
    
    .stat-label {
      font-family: 'Inter', sans-serif;
      font-size: 0.9rem;
      color: rgba(255, 255, 255, 0.6);
      text-transform: uppercase;
      letter-spacing: 1px;
    }
  }
  
  @media (max-width: 768px) {
    gap: 1.5rem;
    
    .stat-item {
      padding: 1rem 1.5rem;
      
      .stat-value {
        font-size: 1.5rem;
      }
      
      .stat-label {
        font-size: 0.8rem;
      }
    }
  }
}

.btn-container {
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  margin: 2rem 0;
  flex-wrap: wrap;
}

.btn-modern {
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  font-size: 1rem;
  padding: 16px 32px;
  border-radius: 12px;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  
  .btn-shine {
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
    transition: left 0.6s ease;
  }
  
  &:hover .btn-shine {
    left: 100%;
  }
  
  &:hover {
    transform: translateY(-2px);
  }
  
  &:active {
    transform: translateY(0);
  }
}

.btn-primary {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  box-shadow: 0 10px 30px rgba(102, 126, 234, 0.3);
  
  &:hover {
    box-shadow: 0 15px 40px rgba(102, 126, 234, 0.4);
  }
}

.btn-secondary {
  background: transparent;
  color: white;
  border: 2px solid rgba(255, 255, 255, 0.3);
  backdrop-filter: blur(10px);
  
  &:hover {
    border-color: rgba(255, 255, 255, 0.5);
    background: rgba(255, 255, 255, 0.1);
  }
}

.social-links-modern {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1.5rem;
  position: relative;
  z-index: 100;
}

.social-icon {
  width: 56px;
  height: 56px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  position: relative;
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border: 2px solid rgba(255, 255, 255, 0.1);
  cursor: pointer;
  pointer-events: auto;
  z-index: 100;
  
  i {
    font-size: 1.3rem;
    color: #fff;
    transition: all 0.3s ease;
    position: relative;
    z-index: 2;
    pointer-events: none;
  }
  
  .tooltip {
    position: absolute;
    bottom: -45px;
    left: 50%;
    transform: translateX(-50%) scale(0.8);
    background: rgba(0, 0, 0, 0.9);
    color: white;
    padding: 8px 14px;
    border-radius: 8px;
    font-size: 0.75rem;
    opacity: 0;
    pointer-events: none;
    transition: all 0.3s ease;
    font-family: 'Inter', sans-serif;
    font-weight: 500;
    white-space: nowrap;
    z-index: 10;
    
    &::before {
      content: '';
      position: absolute;
      top: -5px;
      left: 50%;
      transform: translateX(-50%);
      width: 10px;
      height: 10px;
      background: rgba(0, 0, 0, 0.9);
      transform: translateX(-50%) rotate(45deg);
    }
  }
  
  &::before {
    content: '';
    position: absolute;
    inset: -2px;
    border-radius: 50%;
    padding: 2px;
    background: linear-gradient(135deg, transparent 0%, rgba(255, 255, 255, 0.3) 100%);
    -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
    -webkit-mask-composite: xor;
    mask-composite: exclude;
    opacity: 0;
    transition: opacity 0.3s ease;
  }
  
  &:hover {
    transform: translateY(-8px) rotate(5deg) scale(1.15);
    border-color: rgba(255, 255, 255, 0.3);
    
    &::before {
      opacity: 1;
    }
    
    .tooltip {
      opacity: 1;
      transform: translateX(-50%) scale(1);
      bottom: -50px;
    }
  }
}

.linkedin {
  &:hover {
    background: linear-gradient(135deg, #0077b5 0%, #00a0dc 100%);
    box-shadow: 0 15px 35px rgba(0, 119, 181, 0.4);
  }
}

.github {
  &:hover {
    background: linear-gradient(135deg, #333 0%, #666 100%);
    box-shadow: 0 15px 35px rgba(51, 51, 51, 0.5);
  }
}

.leetcode {
  &:hover {
    background: linear-gradient(135deg, #ffa116 0%, #f89b2f 100%);
    box-shadow: 0 15px 35px rgba(255, 161, 22, 0.4);
  }
}

.gmail {
  &:hover {
    background: linear-gradient(135deg, #ea4335 0%, #d93025 100%);
    box-shadow: 0 15px 35px rgba(234, 67, 53, 0.4);
  }
}

.scroll-indicator {
  position: absolute;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
  opacity: 0.6;
  animation: fadeInOut 3s ease-in-out infinite;
  
  .mouse {
    width: 28px;
    height: 45px;
    border: 2px solid rgba(255, 255, 255, 0.5);
    border-radius: 20px;
    position: relative;
    
    .wheel {
      width: 4px;
      height: 8px;
      background: rgba(255, 255, 255, 0.8);
      border-radius: 2px;
      position: absolute;
      top: 8px;
      left: 50%;
      transform: translateX(-50%);
      animation: scroll-wheel 2s ease-in-out infinite;
    }
  }
  
  p {
    font-family: 'Inter', sans-serif;
    font-size: 0.75rem;
    color: rgba(255, 255, 255, 0.6);
    text-transform: uppercase;
    letter-spacing: 2px;
    margin: 0;
  }
  
  @media (max-width: 768px) {
    display: none;
  }
}

@keyframes scroll-wheel {
  0%, 100% {
    opacity: 0;
    top: 8px;
  }
  50% {
    opacity: 1;
    top: 20px;
  }
}

@keyframes fadeInOut {
  0%, 100% {
    opacity: 0.4;
  }
  50% {
    opacity: 0.8;
  }
}

.pic_container {
  position: relative;
  z-index: 2;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.pic_container_inner.modern-profile {
  height: 450px;
  width: 400px;
  position: relative;
  
  .animated-bg {
    position: absolute;
    height: 380px;
    width: 380px;
    bottom: 30px;
    left: 10px;
    border-radius: 50%;
    background: linear-gradient(45deg, #ff6b6b, #4ecdc4, #45b7d1);
    background-size: 300% 300%;
    animation: gradientRotate 6s ease-in-out infinite;
    filter: blur(2px);
    opacity: 0.8;
  }
  
  .animated-bg-2 {
    position: absolute;
    height: 360px;
    width: 360px;
    bottom: 40px;
    left: 20px;
    border-radius: 50%;
    background: linear-gradient(-45deg, #96ceb4, #ffeaa7, #fd79a8);
    background-size: 300% 300%;
    animation: gradientRotate 8s ease-in-out infinite reverse;
    filter: blur(3px);
    opacity: 0.6;
  }
}

@keyframes gradientRotate {
  0%, 100% { 
    background-position: 0% 50%;
    transform: rotate(0deg) scale(1);
  }
  50% { 
    background-position: 100% 50%;
    transform: rotate(180deg) scale(1.1);
  }
}

.profile-img-modern {
  position: relative;
  z-index: 3;
  border-radius: 50%;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
  transition: all 0.3s ease;
  
  &:hover {
    transform: scale(1.05);
    box-shadow: 0 25px 50px rgba(0, 0, 0, 0.4);
  }
}

// Responsive Design
@media screen and (max-width: 768px) {
  .portfolio-title-3d {
    font-size: 2.5rem;
  }
  
  .scrolling-text span {
    font-size: 1.4rem;
  }
  
  .social-links-modern {
    gap: 1rem;
  }
  
  .social-icon {
    width: 50px;
    height: 50px;
    
    i {
      font-size: 1.2rem;
    }
  }
  
  .btn-container {
    flex-direction: column;
    align-items: center;
    gap: 1rem;
  }
  
  .pic_container_inner.modern-profile {
    height: 350px;
    width: 300px;
    
    .animated-bg,
    .animated-bg-2 {
      height: 280px;
      width: 280px;
    }
  }
}

@media screen and (max-width: 480px) {
  .portfolio-title-3d {
    font-size: 2rem;
    letter-spacing: 1px;
  }
  
  .intro-para {
    font-size: 1rem;
  }
  
  .scrolling-text span {
    font-size: 1.2rem;
    margin-right: 2rem;
  }
}

/* Gradient animation for name title */
@keyframes gradientShift {
  0%, 100% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
}
</style>
