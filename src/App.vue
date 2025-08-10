<template>
  <div id="app" :class="{ 'dark-mode': darkMode }">
    <Nav />
    <Summary />
    <About />
    <Skills />
    <Project/>
    <WriteMe/>
    <Contact />

    <ChatBot/>
    <CanvasAnimation />
  </div>
</template>

<script>
import Nav from "./components/nav.vue";
import Summary from "./components/summary.vue";
import About from "./components/about.vue";
import Skills from "./components/skills_new.vue";
import Project from "./components/project_new.vue";
import Contact from "./components/contact.vue";
import WriteMe from "./components/writeMe.vue";
import ChatBot from "./components/features/chatbot.vue";
import CanvasAnimation from "./components/features/canvas.vue";
import AOS from "aos";

export default {
  components: {
    Nav,
    Summary,
    About,
    Skills,
    Project,
    Contact,
    WriteMe,
    ChatBot,
    CanvasAnimation,
  },
  data() {
    return {
      isScrollDown: false,
      darkMode: sessionStorage.getItem('darkMode') === 'true',
    };
  },
  mounted() {
    // Initialize Zoomtastic if available
    if (typeof Zoomtastic !== 'undefined') {
      Zoomtastic.mount({
        size: '95%',
        easing: 'ease',
        duration: 200, // Reduced duration for better performance
        background: 'rgba(0, 0, 0, 0.9)',
        filter: 'drop-shadow(0 2px 16px rgba(0, 0, 0, 0.3))',
        animation: 'fade' // Simpler animation
      });

      Zoomtastic.listen('[zoomtastic]', 'src');
    }

    // Optimized AOS initialization
    AOS.init({
      duration: 800, // Reduced from default
      easing: 'ease-in-out',
      once: true, // Animation happens only once
      disable: window.innerWidth < 768 // Disable on mobile for performance
    });
  },
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;400;500;600;700&display=swap');

* { 
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Rajdhani", Tahoma, sans-serif;
}

/* Standardized font sizes across the website */
html { 
  font-size: 16px; /* Standard base font size */
}

/* Standard font sizes for consistency */
p, span, li, div {
  font-size: 1rem; /* 16px - consistent across all text */
}

h1 { font-size: 2.5rem; }
h2 { font-size: 2rem; }
h3 { font-size: 1.5rem; }
h4 { font-size: 1.25rem; }
h5 { font-size: 1.1rem; }
h6 { font-size: 1rem; }

/* Remove responsive font size scaling for consistency */
@media (max-width:1200px){ html { font-size:16px; } }
@media (max-width:800px){ html { font-size:16px; } }
@media (max-width:600px){ html { font-size:16px; } }

html, body {
  margin: 0;
  padding: 0;
  width: 100%;
  background: #000000;
  overflow-x: hidden;
  scroll-behavior: smooth; /* Smooth scrolling */
  scroll-snap-type: y mandatory;
}

#app {
  background: #000000;
  background-image: 
    linear-gradient(rgba(255, 255, 255, 0.05) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.05) 1px, transparent 1px),
    linear-gradient(rgba(255, 255, 255, 0.025) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.025) 1px, transparent 1px);
  background-size: 40px 40px, 40px 40px, 10px 10px, 10px 10px;
  background-position: 0 0, 0 0, 0 0, 0 0;
  min-height: 100vh;
  width: 100%;
  position: relative;
  
  /* Simplified background for better performance */
  &::before {
    content: '';
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: 
      radial-gradient(circle at 15% 25%, rgba(64, 255, 218, 0.02) 0%, transparent 30%),
      radial-gradient(circle at 85% 75%, rgba(255, 107, 107, 0.02) 0%, transparent 30%);
    pointer-events: none;
    z-index: -1;
  }
}

/* Simplified animations for better performance */
@keyframes gradientShift {
  0%, 100% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
}

::-webkit-scrollbar {
  width: 12px;
}

::-webkit-scrollbar-track {
  background: #0f0f23;
  border-radius: 10px;
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(45deg, #64ffda, #ff6b6b);
  border-radius: 10px;
  border: 2px solid #0f0f23;
}

::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(45deg, #ff6b6b, #64ffda);
}

::selection {
  background: rgba(100, 255, 218, 0.3);
  color: #fff;
}

.dark-mode {
  background: #0D1117;
  color: white;
  
  #navigation {
    box-shadow: 0 0 20px rgba(100, 255, 218, 0.3) !important;
    backdrop-filter: blur(10px);
  }
  
  .vue-typer {
    .custom.char {
      color: white;
    }
  }
  
  .btn, .btn-color-2 {
    color: white !important;
  }
}

// Section spacing and styling
section {
  position: relative;
  z-index: 1;
  padding: 3rem 0;
  background: transparent !important;
  
  &:not(#summary) {
    background: transparent !important;
    backdrop-filter: none !important;
    border-top: 1px solid rgba(255, 255, 255, 0.08);
    margin-top: 1rem;
  }
}

// Modern glassmorphism cards
.card, .details-container {
  background: rgba(255, 255, 255, 0.05) !important;
  backdrop-filter: blur(15px);
  border: 1px solid rgba(255, 255, 255, 0.15) !important;
  border-radius: 20px !important;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.7) !important;
}

// Improved text readability for all sections
h1, h2, h3, h4, h5, h6 {
  color: #ffffff !important;
  text-shadow: 0 2px 8px rgba(0, 0, 0, 0.8) !important;
  line-height:1.18;
}

p, li, span, a, button {
  color: #e0e6ed !important;
  text-shadow: 0 1px 4px rgba(0, 0, 0, 0.6) !important;
  line-height:1.5;
}

// All sections background consistency
#about, #practicle_skills, #projects, #journey, #contact {
  background: transparent !important;
  
  .container, .container-fluid {
    background: transparent !important;
  }
  
  .row {
    background: transparent !important;
  }
}

// Skills section styling
.skill-item, .tech-icon, .language-item {
  background: rgba(255, 255, 255, 0.05) !important;
  border: 1px solid rgba(255, 255, 255, 0.1) !important;
  color: #ffffff !important;
}

// Project cards styling
.project-card, .project-item {
  background: rgba(255, 255, 255, 0.05) !important;
  border: 1px solid rgba(255, 255, 255, 0.1) !important;
  color: #ffffff !important;
}

// Modern button styles
.btn {
  border-radius: 50px !important;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 1px;
  transition: all 0.3s ease;
  border: none !important;
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

// Navigation improvements
#navigation {
  background: rgba(0, 0, 0, 0.95) !important;
  backdrop-filter: blur(20px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

/* Section spacing optimizations */
section {
  margin-bottom: 0.5rem !important; /* Further reduced gap between sections */
  padding-top: 0.5rem !important; /* Minimal top padding */
  padding-bottom: 0.5rem !important; /* Minimal bottom padding */
  
  &#about {
    margin-top: 0.5rem !important;
    margin-bottom: 0.5rem !important;
  }
  
  &#practicle_skills {
    margin-top: 0.5rem !important;
    margin-bottom: 0.5rem !important;
  }
  
  &#projects {
    margin-top: 0.5rem !important;
    margin-bottom: 0.5rem !important;
  }
  
  &#journey {
    margin-top: 0.5rem !important;
    margin-bottom: 0.5rem !important;
  }
  
  &#contact {
    margin-top: 0.5rem !important;
  }
}

/* Performance optimizations */
* {
  will-change: auto; /* Reset will-change for performance */
}

img {
  image-rendering: -webkit-optimize-contrast; /* Optimize image rendering */
  transform: translateZ(0); /* Hardware acceleration */
}

/* Disable heavy animations and effects for better performance */
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}

/* Optimize scrolling performance */
body {
  -webkit-overflow-scrolling: touch;
}

/* Reduce animation complexity on mobile */
@media (max-width: 768px) {
  #app::before,
  #app::after {
    display: none; /* Remove complex animations on mobile for performance */
  }
  
  section {
    padding: 1rem 0; /* Further reduced padding on mobile */
    margin-bottom: 0.25rem !important; /* Even smaller gaps on mobile */
  }
}

// Responsive design improvements
@media screen and (max-width: 768px) {
  section {
    padding: 2rem 0;
  }
  
  #app {
    background-size: 30px 30px, 30px 30px, 8px 8px, 8px 8px;
  }
}
</style>
