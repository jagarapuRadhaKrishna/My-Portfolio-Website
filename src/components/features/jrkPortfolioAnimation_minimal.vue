<template>
  <transition name="fade">
    <div v-if="show" class="jrk-portfolio-animation" @click="skipAnimation">
      <div class="animation-container">
        <!-- Minimal background accent -->
        <div class="bg-accent"></div>
        
        <!-- Main logo container -->
        <div class="logo-container">
          <!-- JRK text with clean animations -->
          <div class="text-wrapper">
            <span class="jrk-letter" v-for="(letter, index) in 'JRK'" :key="index" :style="getLetterDelay(index)">
              {{ letter }}
            </span>
          </div>
          
          <!-- Portfolio text -->
          <div class="portfolio-wrapper">
            <span class="portfolio-text">PORTFOLIO</span>
          </div>
          
          <!-- Simple underline -->
          <div class="underline"></div>
          
          <!-- Clean progress indicator -->
          <div class="progress-container">
            <div class="progress-dots">
              <div class="dot" v-for="i in 3" :key="i" :class="{ active: currentDot >= i }"></div>
            </div>
            <span class="progress-text">{{ loadingText }}</span>
          </div>
        </div>
        
        <!-- Simple skip button -->
        <button class="skip-btn" @click="skipAnimation">
          Skip
        </button>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'JrkPortfolioAnimation',
  data() {
    return {
      show: true,
      loadingText: 'Loading...',
      loadingSteps: [
        'Loading...',
        'Almost ready...',
        'Welcome!'
      ],
      currentStep: 0,
      currentDot: 0
    };
  },
  mounted() {
    this.startLoadingSequence();
    
    // Auto-hide after animation completes
    setTimeout(() => {
      this.show = false;
    }, 2800);
  },
  methods: {
    startLoadingSequence() {
      const interval = setInterval(() => {
        if (this.currentStep < this.loadingSteps.length - 1) {
          this.currentStep++;
          this.currentDot++;
          this.loadingText = this.loadingSteps[this.currentStep];
        } else {
          clearInterval(interval);
        }
      }, 800);
    },
    skipAnimation() {
      this.show = false;
    },
    getLetterDelay(index) {
      return {
        '--delay': `${index * 0.15}s`
      };
    }
  }
};
</script>

<style scoped>
.jrk-portfolio-animation {
  position: fixed;
  z-index: 9999;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: 
    radial-gradient(circle at 30% 70%, rgba(156, 39, 176, 0.03) 0%, transparent 50%),
    #0a0a0a;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  cursor: pointer;
  font-family: 'Rajdhani', sans-serif;
}

.animation-container {
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Minimal background accent */
.bg-accent {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 400px;
  height: 400px;
  transform: translate(-50%, -50%);
  background: radial-gradient(circle, rgba(156, 39, 176, 0.05) 0%, transparent 70%);
  border-radius: 50%;
  animation: subtlePulse 4s ease-in-out infinite;
}

@keyframes subtlePulse {
  0%, 100% { 
    transform: translate(-50%, -50%) scale(1);
    opacity: 0.3;
  }
  50% { 
    transform: translate(-50%, -50%) scale(1.1);
    opacity: 0.5;
  }
}

/* Main Logo Container */
.logo-container {
  text-align: center;
  position: relative;
  z-index: 10;
}

/* JRK Letters with Clean Animation */
.text-wrapper {
  margin-bottom: 24px;
}

.jrk-letter {
  display: inline-block;
  font-size: clamp(4rem, 8vw, 7rem);
  font-weight: 700;
  color: #ffffff;
  text-shadow: 0 2px 8px rgba(156, 39, 176, 0.3);
  animation: cleanLetterReveal 0.8s var(--delay) cubic-bezier(0.25, 0.46, 0.45, 0.94) forwards;
  opacity: 0;
  transform: translateY(30px);
  margin: 0 0.05em;
  font-family: 'Rajdhani', sans-serif;
}

@keyframes cleanLetterReveal {
  0% {
    opacity: 0;
    transform: translateY(30px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Portfolio Text */
.portfolio-wrapper {
  margin-bottom: 32px;
}

.portfolio-text {
  font-size: clamp(1.1rem, 2.2vw, 1.6rem);
  font-weight: 500;
  color: #9c27b0;
  letter-spacing: 0.25em;
  opacity: 0;
  animation: fadeInUp 0.8s 0.6s ease forwards;
  transform: translateY(20px);
  font-family: 'Rajdhani', sans-serif;
}

@keyframes fadeInUp {
  0% {
    opacity: 0;
    transform: translateY(20px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Simple Underline */
.underline {
  width: 0;
  height: 2px;
  background: linear-gradient(90deg, #9c27b0, #673ab7);
  margin: 0 auto 40px;
  border-radius: 1px;
  animation: underlineExpand 0.8s 1s ease forwards;
}

@keyframes underlineExpand {
  0% { width: 0; }
  100% { width: 120px; }
}

/* Clean Progress Indicator */
.progress-container {
  margin-top: 40px;
  opacity: 0;
  animation: fadeIn 0.5s 1.4s ease forwards;
}

.progress-dots {
  display: flex;
  justify-content: center;
  gap: 12px;
  margin-bottom: 16px;
}

.dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: rgba(156, 39, 176, 0.3);
  transition: all 0.4s ease;
}

.dot.active {
  background: #9c27b0;
  box-shadow: 0 0 12px rgba(156, 39, 176, 0.5);
  transform: scale(1.2);
}

.progress-text {
  font-size: 0.9rem;
  color: #888;
  font-weight: 400;
  letter-spacing: 0.05em;
  font-family: 'Rajdhani', sans-serif;
}

@keyframes fadeIn {
  to { opacity: 1; }
}

/* Simple Skip Button */
.skip-btn {
  position: absolute;
  top: 32px;
  right: 32px;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(156, 39, 176, 0.3);
  color: #9c27b0;
  padding: 10px 20px;
  border-radius: 6px;
  cursor: pointer;
  font-size: 0.85rem;
  font-weight: 500;
  font-family: 'Rajdhani', sans-serif;
  transition: all 0.3s ease;
  opacity: 0;
  animation: fadeIn 0.5s 2s ease forwards;
  backdrop-filter: blur(10px);
}

.skip-btn:hover {
  background: rgba(156, 39, 176, 0.1);
  border-color: #9c27b0;
  transform: translateY(-1px);
  box-shadow: 0 4px 12px rgba(156, 39, 176, 0.2);
}

/* Fade Transition */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.6s ease;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}

/* Responsive Design */
@media (max-width: 768px) {
  .jrk-letter {
    font-size: clamp(3rem, 10vw, 5rem);
  }
  
  .portfolio-text {
    font-size: clamp(1rem, 3.5vw, 1.3rem);
  }
  
  .skip-btn {
    top: 24px;
    right: 24px;
    padding: 8px 16px;
    font-size: 0.8rem;
  }
  
  .bg-accent {
    width: 300px;
    height: 300px;
  }
}

@media (max-width: 480px) {
  .underline {
    width: 100px;
  }
  
  .text-wrapper {
    margin-bottom: 20px;
  }
  
  .portfolio-wrapper {
    margin-bottom: 28px;
  }
}
</style>
