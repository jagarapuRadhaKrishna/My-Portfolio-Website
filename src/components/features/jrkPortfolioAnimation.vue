<template>
  <transition name="fade">
    <div v-if="show" class="jrk-portfolio-animation" @click="skipAnimation">
      <div class="animation-container">
        <!-- Robotic Grid Background -->
        <div class="robotic-grid">
          <div v-for="i in 20" :key="i" class="grid-line" :style="getGridLineStyle(i)"></div>
        </div>
        
        <!-- Scanning Lines -->
        <div class="scan-lines">
          <div class="scan-line" v-for="n in 3" :key="n" :style="getScanLineDelay(n)"></div>
        </div>
        
        <!-- Circuit Pattern -->
        <div class="circuit-pattern">
          <div class="circuit-node" v-for="i in 12" :key="i" :style="getCircuitNodeStyle(i)"></div>
        </div>
        
        <!-- Main logo container -->
        <div class="logo-container">
          <!-- Robotic Frame -->
          <div class="robotic-frame">
            <div class="frame-corner" v-for="i in 4" :key="i" :class="`corner-${i}`"></div>
          </div>
          
          <!-- JRK text with robotic animations -->
          <div class="text-wrapper">
            <div class="letter-container" v-for="(letter, index) in 'JRK'" :key="index">
              <span class="jrk-letter" :style="getLetterDelay(index)">
                {{ letter }}
              </span>
              <div class="letter-glow"></div>
            </div>
          </div>
          
          <!-- Portfolio text with typing effect -->
          <div class="portfolio-wrapper">
            <span class="portfolio-text">{{ displayedPortfolio }}</span>
            <span class="cursor-blink">|</span>
          </div>
          
          <!-- Robotic Underline with segments */
          <div class="underline-container">
            <div class="underline-segment" v-for="i in 5" :key="i" :style="getSegmentDelay(i)"></div>
          </div>
          
          <!-- Loading progress with robotic theme -->
          <div class="progress-container">
            <div class="progress-label">{{ loadingText }}</div>
            <div class="progress-bar-container">
              <div class="progress-bar">
                <div class="progress-fill" :style="`width: ${loadingProgress}%`"></div>
                <div class="progress-scanner"></div>
              </div>
              <span class="progress-percentage">{{ Math.round(loadingProgress) }}%</span>
            </div>
          </div>
        </div>
        
        <!-- Skip button with robotic design -->
        <button class="skip-btn" @click="skipAnimation">
          <div class="btn-frame"></div>
          <span class="btn-text">SKIP</span>
          <div class="btn-arrow">››</div>
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
      loadingText: 'INITIALIZING SYSTEM...',
      loadingSteps: [
        'INITIALIZING SYSTEM...',
        'LOADING NEURAL NETWORK...',
        'CALIBRATING INTERFACE...',
        'ESTABLISHING CONNECTION...',
        'SYSTEM READY'
      ],
      currentStep: 0,
      loadingProgress: 0,
      displayedPortfolio: '',
      portfolioText: 'PORTFOLIO'
    };
  },
  mounted() {
    this.startLoadingSequence();
    this.startTypingEffect();
    this.animateProgress();
    
    // Auto-hide after animation completes
    setTimeout(() => {
      this.show = false;
    }, 4500);
  },
  methods: {
    startLoadingSequence() {
      const interval = setInterval(() => {
        if (this.currentStep < this.loadingSteps.length - 1) {
          this.currentStep++;
          this.loadingText = this.loadingSteps[this.currentStep];
        } else {
          clearInterval(interval);
        }
      }, 700);
    },
    startTypingEffect() {
      setTimeout(() => {
        let index = 0;
        const typeInterval = setInterval(() => {
          if (index < this.portfolioText.length) {
            this.displayedPortfolio += this.portfolioText[index];
            index++;
          } else {
            clearInterval(typeInterval);
          }
        }, 100);
      }, 1500);
    },
    animateProgress() {
      const progressInterval = setInterval(() => {
        if (this.loadingProgress < 100) {
          this.loadingProgress += Math.random() * 3 + 1;
          if (this.loadingProgress > 100) this.loadingProgress = 100;
        } else {
          clearInterval(progressInterval);
        }
      }, 50);
    },
    skipAnimation() {
      this.show = false;
    },
    getLetterDelay(index) {
      return {
        '--delay': `${index * 0.3}s`
      };
    },
    getSegmentDelay(index) {
      return {
        '--delay': `${2 + index * 0.1}s`
      };
    },
    getGridLineStyle(index) {
      const isVertical = index % 2 === 0;
      const position = (index * 10) % 100;
      return {
        '--delay': `${Math.random() * 2}s`,
        '--position': `${position}%`,
        '--orientation': isVertical ? 'vertical' : 'horizontal'
      };
    },
    getScanLineDelay(index) {
      return {
        '--delay': `${index * 0.8}s`
      };
    },
    getCircuitNodeStyle(index) {
      return {
        '--delay': `${index * 0.2}s`,
        left: `${Math.random() * 80 + 10}%`,
        top: `${Math.random() * 80 + 10}%`
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
    radial-gradient(circle at 20% 80%, rgba(220, 20, 60, 0.1) 0%, transparent 50%),
    radial-gradient(circle at 80% 20%, rgba(139, 69, 19, 0.08) 0%, transparent 50%),
    linear-gradient(135deg, #0a0a0a 0%, #1a0a0a 30%, #0f0f0f 70%, #1a1a1a 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  cursor: pointer;
  font-family: 'Orbitron', 'Rajdhani', monospace;
}

.animation-container {
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Robotic Grid Background */
.robotic-grid {
  position: absolute;
  width: 100%;
  height: 100%;
  overflow: hidden;
  opacity: 0.3;
}

.grid-line {
  position: absolute;
  background: linear-gradient(90deg, transparent, #dc143c, transparent);
  animation: gridPulse 3s var(--delay) infinite ease-in-out;
}

.grid-line:nth-child(even) {
  width: 1px;
  height: 100%;
  left: var(--position);
  background: linear-gradient(0deg, transparent, #8b4513, transparent);
}

.grid-line:nth-child(odd) {
  height: 1px;
  width: 100%;
  top: var(--position);
}

@keyframes gridPulse {
  0%, 100% { opacity: 0.1; }
  50% { opacity: 0.6; }
}

/* Scanning Lines */
.scan-lines {
  position: absolute;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

.scan-line {
  position: absolute;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, #dc143c, transparent);
  box-shadow: 0 0 20px #dc143c;
  animation: scanMove 4s var(--delay) infinite linear;
  opacity: 0.7;
}

@keyframes scanMove {
  0% { top: -2px; }
  100% { top: 100%; }
}

/* Circuit Pattern */
.circuit-pattern {
  position: absolute;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

.circuit-node {
  position: absolute;
  width: 4px;
  height: 4px;
  background: #dc143c;
  border-radius: 50%;
  box-shadow: 0 0 10px #dc143c;
  animation: nodePulse 2s var(--delay) infinite ease-in-out;
}

@keyframes nodePulse {
  0%, 100% { 
    opacity: 0.3;
    transform: scale(1);
  }
  50% { 
    opacity: 1;
    transform: scale(1.5);
  }
}

/* Main Logo Container */
.logo-container {
  text-align: center;
  position: relative;
  z-index: 10;
}

/* Robotic Frame */
.robotic-frame {
  position: absolute;
  width: 400px;
  height: 300px;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  pointer-events: none;
}

.frame-corner {
  position: absolute;
  width: 30px;
  height: 30px;
  border: 2px solid #dc143c;
  animation: frameReveal 1s ease forwards;
  opacity: 0;
}

.corner-1 {
  top: 0;
  left: 0;
  border-right: none;
  border-bottom: none;
  animation-delay: 0.5s;
}

.corner-2 {
  top: 0;
  right: 0;
  border-left: none;
  border-bottom: none;
  animation-delay: 0.7s;
}

.corner-3 {
  bottom: 0;
  left: 0;
  border-right: none;
  border-top: none;
  animation-delay: 0.9s;
}

.corner-4 {
  bottom: 0;
  right: 0;
  border-left: none;
  border-top: none;
  animation-delay: 1.1s;
}

@keyframes frameReveal {
  0% {
    opacity: 0;
    transform: scale(0.5);
  }
  100% {
    opacity: 0.8;
    transform: scale(1);
  }
}

/* JRK Letters with Robotic Animation */
.text-wrapper {
  margin-bottom: 20px;
  display: flex;
  justify-content: center;
  gap: 10px;
}

.letter-container {
  position: relative;
}

.jrk-letter {
  display: inline-block;
  font-size: clamp(4rem, 8vw, 7rem);
  font-weight: 900;
  color: #ffffff;
  text-shadow: 
    0 0 10px #dc143c,
    0 0 20px #dc143c,
    0 0 30px #dc143c;
  animation: roboticLetterReveal 1s var(--delay) cubic-bezier(0.68, -0.55, 0.265, 1.55) forwards;
  opacity: 0;
  transform: translateY(50px) rotateX(90deg);
  font-family: 'Orbitron', monospace;
  position: relative;
}

.letter-glow {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(45deg, transparent, #dc143c, transparent);
  opacity: 0;
  animation: letterScan 2s var(--delay) infinite ease-in-out;
  mix-blend-mode: overlay;
}

@keyframes roboticLetterReveal {
  0% {
    opacity: 0;
    transform: translateY(50px) rotateX(90deg) scale(0.8);
    filter: blur(10px);
  }
  50% {
    opacity: 0.8;
    transform: translateY(-5px) rotateX(-5deg) scale(1.05);
    filter: blur(2px);
  }
  100% {
    opacity: 1;
    transform: translateY(0) rotateX(0deg) scale(1);
    filter: blur(0px);
  }
}

@keyframes letterScan {
  0%, 100% { opacity: 0; }
  50% { opacity: 0.3; }
}

/* Portfolio Text with Typing Effect */
.portfolio-wrapper {
  margin-bottom: 30px;
  font-family: 'Orbitron', monospace;
}

.portfolio-text {
  font-size: clamp(1.2rem, 2.5vw, 1.8rem);
  font-weight: 600;
  color: #dc143c;
  letter-spacing: 0.3em;
  text-transform: uppercase;
}

.cursor-blink {
  color: #dc143c;
  animation: blink 1s infinite;
  font-weight: 300;
}

@keyframes blink {
  0%, 50% { opacity: 1; }
  51%, 100% { opacity: 0; }
}

/* Robotic Underline with Segments */
.underline-container {
  display: flex;
  justify-content: center;
  gap: 4px;
  margin: 20px auto;
  width: 200px;
}

.underline-segment {
  width: 36px;
  height: 3px;
  background: linear-gradient(90deg, #8b4513, #dc143c);
  border-radius: 2px;
  opacity: 0;
  animation: segmentReveal 0.3s var(--delay) ease forwards;
  box-shadow: 0 0 5px #dc143c;
}

@keyframes segmentReveal {
  0% {
    opacity: 0;
    transform: scaleX(0);
  }
  100% {
    opacity: 1;
    transform: scaleX(1);
  }
}

/* Robotic Progress Bar */
.progress-container {
  margin-top: 40px;
  opacity: 0;
  animation: fadeInProgress 0.5s 2.5s ease forwards;
}

.progress-label {
  font-size: 0.9rem;
  color: #dc143c;
  font-weight: 500;
  letter-spacing: 0.1em;
  margin-bottom: 15px;
  font-family: 'Orbitron', monospace;
}

.progress-bar-container {
  display: flex;
  align-items: center;
  gap: 15px;
  justify-content: center;
}

.progress-bar {
  width: 250px;
  height: 4px;
  background: rgba(220, 20, 60, 0.2);
  border-radius: 2px;
  position: relative;
  overflow: hidden;
  border: 1px solid rgba(220, 20, 60, 0.3);
}

.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, #8b4513, #dc143c);
  border-radius: 2px;
  transition: width 0.3s ease;
  box-shadow: 0 0 10px #dc143c;
}

.progress-scanner {
  position: absolute;
  top: 0;
  left: -20px;
  width: 20px;
  height: 100%;
  background: linear-gradient(90deg, transparent, #ffffff, transparent);
  animation: scanProgress 1.5s infinite ease-in-out;
}

.progress-percentage {
  font-size: 0.8rem;
  color: #888;
  font-family: 'Orbitron', monospace;
  min-width: 35px;
}

@keyframes scanProgress {
  0% { left: -20px; }
  100% { left: 100%; }
}

@keyframes fadeInProgress {
  to { opacity: 1; }
}

/* Robotic Skip Button */
.skip-btn {
  position: absolute;
  top: 30px;
  right: 30px;
  background: rgba(0, 0, 0, 0.8);
  border: 2px solid #dc143c;
  color: #dc143c;
  padding: 12px 24px;
  cursor: pointer;
  font-size: 0.9rem;
  font-weight: 700;
  font-family: 'Orbitron', monospace;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 10px;
  opacity: 0;
  animation: fadeInSkip 0.5s 3.5s ease forwards;
  position: relative;
  overflow: hidden;
  text-transform: uppercase;
  letter-spacing: 0.1em;
}

.btn-frame {
  position: absolute;
  top: -2px;
  left: -2px;
  right: -2px;
  bottom: -2px;
  background: linear-gradient(45deg, #dc143c, transparent, #dc143c);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.skip-btn:hover .btn-frame {
  opacity: 0.3;
}

.btn-text, .btn-arrow {
  position: relative;
  z-index: 2;
}

.skip-btn:hover {
  background: rgba(220, 20, 60, 0.1);
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(220, 20, 60, 0.3);
}

.btn-arrow {
  transition: transform 0.3s ease;
}

.skip-btn:hover .btn-arrow {
  transform: translateX(3px);
}

@keyframes fadeInSkip {
  to { opacity: 1; }
}

/* Fade Transition */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.8s cubic-bezier(0.4, 0, 0.2, 1);
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}

/* Responsive Design */
@media (max-width: 768px) {
  .jrk-letter {
    font-size: clamp(3rem, 12vw, 5rem);
  }
  
  .portfolio-text {
    font-size: clamp(1rem, 4vw, 1.3rem);
  }
  
  .progress-bar {
    width: 200px;
  }
  
  .skip-btn {
    top: 20px;
    right: 20px;
    padding: 10px 18px;
    font-size: 0.8rem;
  }
  
  .robotic-frame {
    width: 300px;
    height: 200px;
  }
}

@media (max-width: 480px) {
  .underline-container {
    width: 150px;
  }
  
  .progress-bar {
    width: 150px;
  }
  
  .text-wrapper {
    gap: 5px;
  }
}
</style>
