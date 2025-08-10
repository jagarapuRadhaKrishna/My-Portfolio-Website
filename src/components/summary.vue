<template>
  <section id="summary" class="section section_1 py-5 w-100 modern-hero">
    <div class="container-fluid">
      <div class="row min-vh-100 align-items-center">
        <div data-aos="fade-up" data-aos-duration="1000" class="col-12 px-4 py-5 d-flex justify-content-start align-items-center flex-column hero-content">
          <div class="main-title">
            <h1 class="name-title">Jagarapu Radha Krishna</h1>
          </div>
          
          <div class="scrolling-text-container">
            <div class="scrolling-text">
              <span>Software Engineer</span>
              <span>Full Stack Developer</span>
              <span>Backend Developer (Java Spring Boot, Node.js)</span>
              <span>Data Enthusiast</span>
              <span>AI & ML Engineer</span>
              <span>Software Engineer</span>
              <span>Full Stack Developer</span>
              <span>Backend Developer (Java Spring Boot, Node.js)</span>
              <span>Data Enthusiast</span>
              <span>AI & ML Engineer</span>
            </div>
          </div>

          <p class="intro-para mt-4"> 
            Versatile Software Engineer crafting high-performance, scalable, and secure applications across Full Stack and Backend ecosystems. Proficient in Java Spring Boot, Node.js, Next.js, and React, with deep expertise in REST API architecture, cloud-ready systems, and database optimization for PostgreSQL, MongoDB, and MySQL.
          </p>
          <p class='intro-para'>
            Experienced in building AI-powered solutions that blend machine learning, NLP, and automation to deliver real-world impact — from intelligent career platforms to real-time trading systems. Top 10% LeetCode performer with proven DSA mastery and a track record of transforming complex challenges into elegant, user-focused solutions.
          </p>

          <div class="btn-container mt-4">
            <button
              class="btn btn-modern btn-resume"
              onclick="location.href='https://drive.google.com/file/d/1lmklnLJ3cSxYzAYWyqsZxZ0m-VClKhEd/view?usp=sharing'"
            >
              <i class="fas fa-download mr-2"></i>View Resume
            </button>
            <button class="btn btn-modern btn-contact" @click="scrollToSection('contact')">
              <i class="fas fa-envelope mr-2"></i>Contact Info
            </button>
          </div>

          <div class="social-links-modern">
            <a href="https://www.linkedin.com/in/jagarapuradhakrishna" target="_blank" class="social-icon linkedin">
              <i class="fab fa-linkedin-in"></i>
              <span class="tooltip">LinkedIn</span>
            </a>
            <a href="https://github.com/jagarapuRadhaKrishna" target="_blank" class="social-icon github">
              <i class="fab fa-github"></i>
              <span class="tooltip">GitHub</span>
            </a>
            <a href="https://leetcode.com/u/Radhakrishna02256/" target="_blank" class="social-icon leetcode">
              <i class="fas fa-code"></i>
              <span class="tooltip">LeetCode</span>
            </a>
            <a href="mailto:radhakrishna02256@gmail.com" class="social-icon gmail">
              <i class="fas fa-envelope"></i>
              <span class="tooltip">Gmail</span>
            </a>
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
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;400;500;600;700&display=swap');

.modern-hero {
  background: transparent;
  min-height: 100vh;
  position: relative;
  overflow: hidden;
  display: flex;
  align-items: center;
  padding-top: 50px;
}

.hero-content {
  align-items: flex-start !important;
  text-align: left !important;
  padding-left: 1.5rem !important;
  
  @media (max-width: 768px) {
    align-items: center !important;
    text-align: center !important;
    padding-left: 1rem !important;
  }
}

.section__text {
  position: relative;
  z-index: 2;
  height: 100%;
  
  .intro-para {
    max-width: 700px;
    font-family: 'Rajdhani', sans-serif;
    font-weight: 400;
    font-size: 1.3rem;
    line-height: 1.8;
    color: #ffffff;
    text-align: left;
    margin: 0;
    
    @media (max-width: 768px) {
      text-align: center;
      color: #e0e6ed;
    }
  }
}

.main-title {
  margin-bottom: 2rem;
}

.name-title {
  font-family: 'Orbitron', 'Helvetica', sans-serif;
  font-size: 3rem;
  font-weight: 900;
  color: white !important;
  text-align: left;
  letter-spacing: 3px;
  text-transform: uppercase;
  margin-bottom: 1.5rem;
  text-shadow: 
    0 0 10px rgba(255, 255, 255, 0.8),
    0 0 20px rgba(255, 255, 255, 0.5),
    0 0 30px rgba(255, 255, 255, 0.3),
    3px 3px 6px rgba(0, 0, 0, 0.8);
  background: linear-gradient(45deg, #ffffff, #f0f0f0, #e8e8e8, #ffffff);
  background-size: 200% 200%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  position: relative;
  animation: gradientShift 4s ease-in-out infinite;
  
  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: linear-gradient(45deg, rgba(255, 255, 255, 0.05), transparent);
    border-radius: 8px;
    z-index: -1;
  }
  
  @media (max-width: 768px) {
    font-size: 2.2rem;
    letter-spacing: 2px;
    text-align: center;
  }
  
  @media (max-width: 480px) {
    font-size: 1.8rem;
    letter-spacing: 1px;
  }
}

.scrolling-text-container {
  height: 60px;
  overflow: hidden;
  margin: 1.5rem 0;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  width: 100%;
  
  @media (max-width: 768px) {
    justify-content: center;
  }
}

.scrolling-text {
  animation: scroll 20s linear infinite;
  white-space: nowrap;
  
  span {
    display: inline-block;
    font-family: 'Rajdhani', sans-serif;
    font-size: 1.8rem;
    font-weight: 500;
    color: #ffffff;
    margin-right: 4rem;
    opacity: 0.9;
    text-shadow: 0 0 5px rgba(255, 255, 255, 0.3);
    
    &:nth-child(odd) {
      color: #ffffff;
    }
    
    &:nth-child(even) {
      color: #cccccc;
    }
    
    @media (max-width: 768px) {
      font-size: 1.4rem;
      margin-right: 3rem;
    }
  }
}

@keyframes scroll {
  0% { transform: translateX(100vw); }
  100% { transform: translateX(-100%); }
}

.btn-container {
  display: flex;
  justify-content: flex-start;
  gap: 1.5rem;
  margin: 1.5rem 0;
  
  @media (max-width: 768px) {
    justify-content: center;
  }
}

.btn-modern {
  font-family: 'Rajdhani', sans-serif;
  font-weight: 600;
  font-size: 1.1rem;
  padding: 15px 30px;
  border-radius: 50px;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
  text-transform: uppercase;
  letter-spacing: 1px;
  position: relative;
  overflow: hidden;
  
  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
    transition: left 0.5s;
  }
  
  &:hover::before {
    left: 100%;
  }
}

.btn-resume {
  background: linear-gradient(45deg, #ff6b6b, #ee5a52);
  color: white;
  box-shadow: 0 8px 20px rgba(255, 107, 107, 0.3);
  
  &:hover {
    transform: translateY(-3px);
    box-shadow: 0 12px 25px rgba(255, 107, 107, 0.4);
  }
}

.btn-contact {
  background: linear-gradient(45deg, #4ecdc4, #44a08d);
  color: white;
  box-shadow: 0 8px 20px rgba(78, 205, 196, 0.3);
  
  &:hover {
    transform: translateY(-3px);
    box-shadow: 0 12px 25px rgba(78, 205, 196, 0.4);
  }
}

.social-links-modern {
  display: flex;
  justify-content: flex-start;
  gap: 2rem;
  margin-top: 2rem;
  
  @media (max-width: 768px) {
    justify-content: center;
  }
}

.social-icon {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  transition: all 0.3s ease;
  position: relative;
  backdrop-filter: blur(10px);
  border: 2px solid rgba(255, 255, 255, 0.2);
  
  i {
    font-size: 1.5rem;
    color: #fff;
    transition: all 0.3s ease;
  }
  
  .tooltip {
    position: absolute;
    bottom: -40px;
    left: 50%;
    transform: translateX(-50%);
    background: rgba(0, 0, 0, 0.8);
    color: white;
    padding: 5px 10px;
    border-radius: 5px;
    font-size: 0.8rem;
    opacity: 0;
    transition: all 0.3s ease;
    font-family: 'Rajdhani', sans-serif;
  }
  
  &:hover .tooltip {
    opacity: 1;
    bottom: -35px;
  }
  
  &:hover {
    transform: translateY(-5px) scale(1.1);
  }
}

.linkedin {
  background: linear-gradient(45deg, #0077b5, #00a0dc);
  box-shadow: 0 8px 20px rgba(0, 119, 181, 0.3);
  
  &:hover {
    box-shadow: 0 12px 25px rgba(0, 119, 181, 0.4);
  }
}

.github {
  background: linear-gradient(45deg, #333, #555);
  box-shadow: 0 8px 20px rgba(51, 51, 51, 0.3);
  
  &:hover {
    box-shadow: 0 12px 25px rgba(51, 51, 51, 0.4);
  }
}

.leetcode {
  background: linear-gradient(45deg, #ffa116, #f89b2f);
  box-shadow: 0 8px 20px rgba(255, 161, 22, 0.3);
  
  &:hover {
    box-shadow: 0 12px 25px rgba(255, 161, 22, 0.4);
  }
}

.gmail {
  background: linear-gradient(45deg, #ea4335, #d93025);
  box-shadow: 0 8px 20px rgba(234, 67, 53, 0.3);
  
  &:hover {
    box-shadow: 0 12px 25px rgba(234, 67, 53, 0.4);
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
