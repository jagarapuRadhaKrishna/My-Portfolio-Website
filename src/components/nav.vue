<template>
  <nav id="navigation" class="modern-nav">
    <div class="container-fluid px-4">
      <div class="nav-wrapper">
        <div class="logo-section">
          <h2 class="logo-text" @click="scrollToSection('summary')">
            <span class="logo-icon">RK</span>
            <span class="logo-divider">|</span>
            <span class="logo-name">Portfolio</span>
          </h2>
        </div>

        <div class="nav-center">
          <ul class="nav-links">
            <li class="nav-item" :class="{ active: activeSection === 'summary' }" @click="scrollToSection('summary')">
              <span class="nav-text">Home</span>
              <span class="nav-indicator"></span>
            </li>
            <li class="nav-item" :class="{ active: activeSection === 'about' }" @click="scrollToSection('about')">
              <span class="nav-text">About</span>
              <span class="nav-indicator"></span>
            </li>
            <li class="nav-item" :class="{ active: activeSection === 'practicle_skills' }" @click="scrollToSection('practicle_skills')">
              <span class="nav-text">Skills</span>
              <span class="nav-indicator"></span>
            </li>
            <li class="nav-item" :class="{ active: activeSection === 'projects' }" @click="scrollToSection('projects')">
              <span class="nav-text">Projects</span>
              <span class="nav-indicator"></span>
            </li>
            <li class="nav-item" :class="{ active: activeSection === 'contact' }" @click="scrollToSection('contact')">
              <span class="nav-text">Contact</span>
              <span class="nav-indicator"></span>
            </li>
          </ul>
        </div>

        <div class="nav-actions">
          <button class="theme-toggle" @click="toggleDarkMode()">
            <i class="fas fa-moon" v-if="!darkMode"></i>
            <i class="fas fa-sun" v-if="darkMode"></i>
          </button>
          <button class="mobile-menu-toggle" @click="toggleMobileMenu">
            <span class="hamburger-line"></span>
            <span class="hamburger-line"></span>
            <span class="hamburger-line"></span>
          </button>
        </div>
      </div>
    </div>

    <div class="mobile-nav" :class="{ active: mobileMenuOpen }">
      <ul class="mobile-nav-links">
        <li class="mobile-nav-item" @click="scrollToSection('summary'); toggleMobileMenu()">
          <i class="fas fa-home"></i>
          <span>Home</span>
        </li>
        <li class="mobile-nav-item" @click="scrollToSection('about'); toggleMobileMenu()">
          <i class="fas fa-user"></i>
          <span>About</span>
        </li>
        <li class="mobile-nav-item" @click="scrollToSection('practicle_skills'); toggleMobileMenu()">
          <i class="fas fa-code"></i>
          <span>Skills</span>
        </li>
        <li class="mobile-nav-item" @click="scrollToSection('projects'); toggleMobileMenu()">
          <i class="fas fa-briefcase"></i>
          <span>Projects</span>
        </li>
        <li class="mobile-nav-item" @click="scrollToSection('contact'); toggleMobileMenu()">
          <i class="fas fa-envelope"></i>
          <span>Contact</span>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      darkMode: sessionStorage.getItem('darkMode') === 'true',
      activeSection: 'summary',
      mobileMenuOpen: false,
    };
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    toggleDarkMode() {
      this.darkMode = !this.darkMode;
      sessionStorage.setItem('darkMode', this.darkMode.toString());

      if (this.darkMode) {
        document.getElementById('app').classList.add('dark-mode');
      } else {
        document.getElementById('app').classList.remove('dark-mode');
      }
    },
    scrollToSection(sectionId) {
      this.activeSection = sectionId;
      const element = document.getElementById(sectionId);
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' });
      }
    },
    toggleMobileMenu() {
      this.mobileMenuOpen = !this.mobileMenuOpen;
      if (this.mobileMenuOpen) {
        document.body.style.overflow = 'hidden';
      } else {
        document.body.style.overflow = '';
      }
    },
    handleScroll() {
      const sections = ['summary', 'about', 'practicle_skills', 'projects', 'contact'];
      const scrollPosition = window.scrollY + 100;

      for (const sectionId of sections) {
        const element = document.getElementById(sectionId);
        if (element) {
          const offsetTop = element.offsetTop;
          const height = element.offsetHeight;

          if (scrollPosition >= offsetTop && scrollPosition < offsetTop + height) {
            this.activeSection = sectionId;
            break;
          }
        }
      }
    }
  },
};
</script>

<style lang="scss" scoped>

.modern-nav {
  background: rgba(10, 10, 20, 0.8);
  backdrop-filter: blur(20px) saturate(180%);
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: 1rem 0;
  transition: all 0.3s ease;
  
  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, rgba(102, 126, 234, 0.5), transparent);
    opacity: 0;
    transition: opacity 0.3s ease;
  }
  
  &:hover::before {
    opacity: 1;
  }
}

.nav-wrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 2rem;
}

.logo-section {
  .logo-text {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 1.4rem;
    font-weight: 700;
    color: #ffffff;
    margin: 0;
    cursor: pointer;
    display: flex;
    align-items: center;
    gap: 0.75rem;
    transition: all 0.3s ease;
    
    .logo-icon {
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      padding: 0.4rem 0.8rem;
      border-radius: 8px;
      font-weight: 700;
      letter-spacing: -1px;
    }
    
    .logo-divider {
      color: rgba(255, 255, 255, 0.3);
    }
    
    .logo-name {
      color: rgba(255, 255, 255, 0.9);
      font-weight: 500;
    }
    
    &:hover {
      transform: translateX(3px);
      
      .logo-icon {
        box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
      }
    }
  }
}

.nav-center {
  flex: 1;
  display: flex;
  justify-content: center;
  
  @media (max-width: 992px) {
    display: none;
  }
}

.nav-links {
  list-style: none;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin: 0;
  padding: 0;
}

.nav-item {
  font-family: 'Inter', sans-serif;
  font-weight: 500;
  font-size: 0.95rem;
  color: rgba(255, 255, 255, 0.7);
  cursor: pointer;
  padding: 0.6rem 1.2rem;
  border-radius: 10px;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  
  .nav-text {
    position: relative;
    z-index: 2;
  }
  
  .nav-indicator {
    position: absolute;
    bottom: 8px;
    left: 50%;
    transform: translateX(-50%) scaleX(0);
    width: 20px;
    height: 2px;
    background: linear-gradient(90deg, #667eea, #764ba2);
    border-radius: 2px;
    transition: transform 0.3s ease;
  }
  
  &::before {
    content: '';
    position: absolute;
    inset: 0;
    background: rgba(255, 255, 255, 0.05);
    border-radius: 10px;
    opacity: 0;
    transition: opacity 0.3s ease;
  }
  
  &:hover {
    color: rgba(255, 255, 255, 1);
    
    &::before {
      opacity: 1;
    }
  }
  
  &.active {
    color: rgba(255, 255, 255, 1);
    background: rgba(255, 255, 255, 0.08);
    
    .nav-indicator {
      transform: translateX(-50%) scaleX(1);
    }
  }
}

.nav-actions {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.theme-toggle {
  width: 42px;
  height: 42px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s ease;
  color: rgba(255, 255, 255, 0.8);
  
  i {
    font-size: 1.1rem;
  }
  
  &:hover {
    background: rgba(255, 255, 255, 0.1);
    border-color: rgba(255, 255, 255, 0.2);
    transform: rotate(15deg) scale(1.1);
  }
}

.mobile-menu-toggle {
  width: 42px;
  height: 42px;
  border-radius: 10px;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  display: none;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 5px;
  cursor: pointer;
  transition: all 0.3s ease;
  
  .hamburger-line {
    width: 20px;
    height: 2px;
    background: rgba(255, 255, 255, 0.8);
    border-radius: 2px;
    transition: all 0.3s ease;
  }
  
  &:hover {
    background: rgba(255, 255, 255, 0.1);
    border-color: rgba(255, 255, 255, 0.2);
  }
  
  @media (max-width: 992px) {
    display: flex;
  }
}

.mobile-nav {
  position: fixed;
  top: 0;
  right: -100%;
  width: 280px;
  height: 100vh;
  background: rgba(10, 10, 20, 0.98);
  backdrop-filter: blur(20px);
  border-left: 1px solid rgba(255, 255, 255, 0.1);
  padding: 6rem 2rem 2rem;
  transition: right 0.3s ease;
  z-index: 999;
  overflow-y: auto;
  
  &.active {
    right: 0;
  }
  
  @media (min-width: 993px) {
    display: none;
  }
}

.mobile-nav-links {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.mobile-nav-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem 1.5rem;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 12px;
  color: rgba(255, 255, 255, 0.8);
  cursor: pointer;
  transition: all 0.3s ease;
  font-family: 'Inter', sans-serif;
  font-weight: 500;
  
  i {
    font-size: 1.2rem;
    width: 24px;
    text-align: center;
    color: #667eea;
  }
  
  &:hover {
    background: rgba(255, 255, 255, 0.1);
    color: rgba(255, 255, 255, 1);
    transform: translateX(5px);
  }
}

@media screen and (max-width: 768px) {
  .modern-nav {
    padding: 0.75rem 0;
  }
  
  .logo-section .logo-text {
    font-size: 1.2rem;
    
    .logo-icon {
      padding: 0.3rem 0.6rem;
    }
  }
}
</style>
