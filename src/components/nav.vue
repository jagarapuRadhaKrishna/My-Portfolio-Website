<template>
  <div id="navigation" class="py-1 shadow nav modern-nav">
    <div class="container-fluid px-3 d-flex justify-content-between align-items-center">
      <h2 class="portfolio-title-nav">MY PORTFOLIO</h2>
      <ul class="d-flex mb-0 nav-links">
        <li class="p-2 scroll-to nav-item" @click="scrollToSection('summary')">Home</li>
        <li class="p-2 scroll-to nav-item" @click="scrollToSection('about')">About</li>
        <li class="p-2 scroll-to nav-item" @click="scrollToSection('practicle_skills')">Skills</li>
        <li class="p-2 scroll-to nav-item" @click="scrollToSection('projects')">Projects</li>
        <li class="p-2 scroll-to nav-item" @click="scrollToSection('contact')">Contact</li>

        <li class="pt-2 pl-3">
          <input type="checkbox" class="checkbox" id="checkbox" v-model="darkMode" @change="toggleDarkMode()">
          <label for="checkbox" class="checkbox-label">
            <i class="fas fa-moon"></i>
            <i class="fas fa-sun"></i>
            <span class="ball"></span>
          </label>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      darkMode: sessionStorage.getItem('darkMode') === 'true',
    };
  },
  methods: {
    toggleDarkMode() {
      sessionStorage.setItem('darkMode', this.darkMode.toString());

      if (this.darkMode) {
        $('#app').addClass('dark-mode');
      } else {
        $('#app').removeClass('dark-mode');
      }
    },
    scrollToSection(sectionId) {
      const element = document.getElementById(sectionId);
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' });
      }
    }
  },
};
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;400;500;600;700&display=swap');

.modern-nav {
  background: rgba(0, 0, 0, 0.95) !important;
  backdrop-filter: blur(20px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5) !important;
}

.portfolio-title-nav {
  font-family: 'Orbitron', monospace;
  font-size: 1.4rem;
  font-weight: 900;
  color: #ffffff;
  text-transform: uppercase;
  letter-spacing: 1px;
  text-shadow: 
    0 0 5px rgba(255, 255, 255, 0.3),
    0 0 10px rgba(255, 255, 255, 0.2),
    0 0 15px rgba(255, 255, 255, 0.1);
  margin: 0;
  display: inline-block;
  transition: all 0.3s ease;
  
  &:hover {
    color: #ffffff;
    text-shadow: 
      0 0 5px rgba(255, 255, 255, 0.6),
      0 0 10px rgba(255, 255, 255, 0.4),
      0 0 15px rgba(255, 255, 255, 0.3),
      0 0 20px rgba(255, 255, 255, 0.2);
    transform: scale(1.02);
  }
}

@keyframes gradientShift {
  0%, 100% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
}

.nav-links {
  list-style: none;
  display: flex;
  align-items: center;
  gap: 1rem;
  margin: 0;
  padding: 0;
}

.nav-item {
  font-family: 'Rajdhani', sans-serif;
  font-weight: 600;
  font-size: 1rem;
  color: #ffffff !important;
  cursor: pointer;
  padding: 6px 12px !important;
  border-radius: 20px;
  transition: all 0.3s ease;
  position: relative;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  
  &::before {
    content: '';
    position: absolute;
    bottom: 0;
    left: 50%;
    width: 0;
    height: 2px;
    background: #ffffff;
    transition: all 0.3s ease;
    transform: translateX(-50%);
  }
  
  &:hover {
    color: #000000 !important;
    text-decoration: none;
    transform: translateY(-2px);
    background: rgba(255, 255, 255, 0.9);
    box-shadow: 0 4px 15px rgba(255, 255, 255, 0.3);
    
    &::before {
      width: 80%;
    }
  }
  
  &:active {
    transform: translateY(0);
  }
}

.checkbox {
  opacity: 0;
  position: absolute;
}

.checkbox-label {
  background: linear-gradient(45deg, #2c3e50, #34495e);
  width: 45px;
  height: 25px;
  border-radius: 50px;
  position: relative;
  padding: 2px;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 2px solid rgba(255, 255, 255, 0.3);
  transition: all 0.3s ease;
  margin-left: 0.3rem;
  
  &:hover {
    border-color: rgba(255, 255, 255, 0.6);
    box-shadow: 0 0 8px rgba(255, 255, 255, 0.2);
  }
  
  .ball {
    background: linear-gradient(45deg, #ffffff, #f0f0f0);
    width: 19px;
    height: 19px;
    position: absolute;
    left: 2px;
    top: 2px;
    border-radius: 50%;
    transition: transform 0.3s ease;
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.3);
  }
  
  i {
    font-size: 0.7rem;
    z-index: 2;
    transition: all 0.3s ease;
  }
}

.fa-moon {
  color: #f1c40f;
  margin-left: 4px;
}

.fa-sun {
  color: #f39c12;
  margin-right: 4px;
}

.checkbox:checked + .checkbox-label {
  background: linear-gradient(45deg, #e74c3c, #c0392b);
  
  .ball {
    transform: translateX(25px);
    background: linear-gradient(45deg, #ff6b6b, #ee5a52);
  }
}

// Mobile responsive
@media screen and (max-width: 768px) {
  .modern-nav {
    padding: 0.5rem 0 !important;
  }
  
  .portfolio-title-nav {
    font-size: 1.4rem;
    letter-spacing: 1px;
  }
  
  .nav-links {
    gap: 0.5rem;
  }
  
  .nav-item {
    font-size: 0.9rem;
    padding: 6px 12px !important;
  }
  
  .checkbox-label {
    width: 45px;
    height: 25px;
    
    .ball {
      width: 19px;
      height: 19px;
    }
    
    i {
      font-size: 0.8rem;
    }
  }
  
  .checkbox:checked + .checkbox-label .ball {
    transform: translateX(20px);
  }
}

@media screen and (max-width: 480px) {
  .nav-item:nth-child(2),
  .nav-item:nth-child(3) {
    display: none;
  }
  
  .portfolio-title-nav {
    font-size: 1.2rem;
  }
  
  .nav-item {
    font-size: 0.8rem;
    padding: 4px 8px !important;
  }
}

// Add some top margin to body to account for fixed nav
body {
  padding-top: 80px;
}
</style>
