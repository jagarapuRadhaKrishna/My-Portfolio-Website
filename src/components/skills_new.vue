<template>
  <div class="skills-wrapper">
    <section id="practicle_skills">
      <Heading :title="'Technical Skills'" :subtitle="'Explore My'" />
      <div class="container">
        <!-- Icons Section -->
        <div class="icons-section">
          <div
            v-for="(skill, index) in iconSkills"
            :key="skill.name || index"
            class="icon-item"
          >
            <img
              v-if="skill.hasIcon"
              :src="`/icons/${skill.imageSrc}.${skill.extension || 'png'}`"
              class="skill-image"
              @error="handleImageError"
              :alt="skill.name"
            />
            <span
              v-else
              class="skill-icon-fallback"
            >
              {{ getIconEmoji(skill.category) }}
            </span>
            <span class="skill-name">{{ skill.name }}</span>
            <span v-if="skill.subtitle" class="skill-subtitle">{{ skill.subtitle }}</span>
          </div>
        </div>

        <!-- Card Skills Section -->
        <div class="cards-section">
          <div
            v-for="(skill, index) in cardSkills"
            :key="skill.name || index"
            class="skill-card dark-card"
          >
            <img
              v-if="skill.hasIcon"
              :src="`/icons/${skill.imageSrc}.${skill.extension || 'png'}`"
              class="skill-image"
              @error="handleImageError"
              :alt="skill.name"
            />
            <span
              v-else
              class="skill-icon-fallback"
            >
              {{ getIconEmoji(skill.category) }}
            </span>
            <span class="skill-name">{{ skill.name }}</span>
            <span v-if="skill.subtitle" class="skill-subtitle">{{ skill.subtitle }}</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Certifications Section -->
    <section id="certifications" class="certifications-section">
      <Heading :title="'Certifications'" :subtitle="'Professional'" />
      <div class="container">
        <div class="certifications-grid">
          <!-- First Row - Java SpringBoot & Software Development -->
          <div class="certification-card">
            <div class="cert-image-container">
              <img 
                src="/java-cert.png" 
                alt="Java SpringBoot Certificate" 
                class="cert-image" 
                @error="handleCertificateError"
                @load="handleImageLoad"
                @click="openCertificateModal('java')"
              />
            </div>
            <div class="cert-info">
              <h3 class="cert-title">Java SpringBoot</h3>
              <p class="cert-issuer">Infosys Springboard</p>
            </div>
          </div>

          <div class="certification-card">
            <div class="cert-image-container">
              <img 
                src="/software-dev-cert.jpg" 
                alt="Software Development Certificate" 
                class="cert-image" 
                @error="handleCertificateError"
                @load="handleImageLoad"
                @click="openCertificateModal('software')"
              />
            </div>
            <div class="cert-info">
              <h3 class="cert-title">Software Development</h3>
              <p class="cert-issuer">Citi</p>
            </div>
          </div>

          <div class="certification-card">
            <div class="cert-image-container">
              <img 
                src="/data-analytics-cert.jpg" 
                alt="Data Analytics Certificate" 
                class="cert-image" 
                @error="handleCertificateError"
                @load="handleImageLoad"
                @click="openCertificateModal('data')"
              />
            </div>
            <div class="cert-info">
              <h3 class="cert-title">Data Analytics</h3>
              <p class="cert-issuer">Deloitte</p>
            </div>
          </div>

          <!-- Second Row - Only Google Analytics -->
          <div class="certification-card">
            <div class="cert-image-container">
              <img 
                src="/google-analytics-cert.jpg" 
                alt="Google Analytics Certificate" 
                class="cert-image" 
                @error="handleCertificateError"
                @load="handleImageLoad"
                @click="openCertificateModal('google')"
              />
            </div>
            <div class="cert-info">
              <h3 class="cert-title">Google Analytics</h3>
              <p class="cert-issuer">Google</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Certificate Modal -->
    <div v-if="showCertModal && currentCertificate" class="certificate-modal-overlay" @click="closeCertificateModal">
      <div class="certificate-modal-content" @click.stop>
        <button class="modal-close-btn" @click="closeCertificateModal">&times;</button>
        <img :src="currentCertificate.src" :alt="`${currentCertificate.title} Certificate - Full View`" class="modal-cert-image" />
      </div>
    </div>
  </div>
</template>

<script>
import Heading from "./common/heading.vue";
export default {
  components: {
    Heading,
  },
  data() {
    return {
      skills: [
        // Icons Only - No Background Skills (First Section)
        { name: 'Java', imageSrc: 'java_new', hasIcon: true, extension: 'svg' },
        { name: 'JavaScript', imageSrc: 'js', hasIcon: true, extension: 'png' },
        { name: 'Python', subtitle: '(ML, Scikit-learn, NumPy, Pandas, Matplotlib, Seaborn, Plotly)', imageSrc: 'python', hasIcon: true, extension: 'png' },
        { name: 'Spring Boot', imageSrc: 'springboot', hasIcon: true, extension: 'svg' },
        { name: 'Node.js & Express.js', imageSrc: 'nodejs_express', hasIcon: true, extension: 'svg' },
        { name: 'HTML', imageSrc: 'html', hasIcon: true, extension: 'png' },
        { name: 'CSS', imageSrc: 'css', hasIcon: true, extension: 'png' },
        { name: 'Tailwind CSS', imageSrc: 'tailwind', hasIcon: true, extension: 'svg' },
        { name: 'MySQL', imageSrc: 'mysql', hasIcon: true, extension: 'svg' },
        { name: 'MongoDB', imageSrc: 'mongodb', hasIcon: true, extension: 'svg' },
        { name: 'SQL', imageSrc: 'sql', hasIcon: true, extension: 'svg' },
        { name: 'NLP', subtitle: '(BERT, Word Segmentation)', imageSrc: 'nlp', hasIcon: true, extension: 'svg' },
        { name: 'Git', imageSrc: 'git', hasIcon: true, extension: 'png' },
        
        // Card Style Skills (Second Section)
        { name: 'REST APIs', imageSrc: 'api', hasIcon: true, extension: 'png' },
        { name: 'Data Structures & Algorithms (OOP)', imageSrc: 'dsa_oop', hasIcon: true, extension: 'svg' },
        { name: 'System Design', imageSrc: 'system_design', hasIcon: true, extension: 'svg' }
      ],
      showCertModal: false,
      currentCertificate: null,
      certificates: {
        java: { src: '/java-cert.png', title: 'Java SpringBoot', issuer: 'Infosys Springboard' },
        software: { src: '/software-dev-cert.jpg', title: 'Software Development', issuer: 'Citi' },
        data: { src: '/data-analytics-cert.jpg', title: 'Data Analytics', issuer: 'Deloitte' },
        google: { src: '/google-analytics-cert.jpg', title: 'Google Analytics', issuer: 'Google' }
      }
    };
  },
  computed: {
    iconSkills() {
      return this.skills.filter(skill => this.isNoBackgroundSkill(skill.name));
    },
    cardSkills() {
      return this.skills.filter(skill => this.isDarkCardSkill(skill.name));
    }
  },
  methods: {
    toggleSkillLevel(index) {
      this.$set(this.skills, index, { ...this.skills[index], showLevel: !this.skills[index].showLevel });
    },
    getAosDuration(index) {
      return (index * 200) + 400;
    },
    getSkillsByCategory(categories) {
      return this.skills.filter(skill => categories.includes(skill.category));
    },
    handleImageError(event) {
      // Try to fallback to SVG version first, then hide
      const img = event.target;
      const currentSrc = img.src;
      
      if (currentSrc.includes('.png')) {
        // Try SVG version
        const svgSrc = currentSrc.replace('.png', '.svg');
        img.src = svgSrc;
      } else {
        // If SVG also fails, hide the image and show fallback
        img.style.display = 'none';
        const fallback = img.nextElementSibling;
        if (fallback && fallback.classList.contains('skill-icon-fallback')) {
          fallback.style.display = 'inline-block';
        }
      }
    },
    getIconEmoji(category) {
      const emojiMap = {
        'backend': '⚙️',
        'programming': '💻',
        'frontend': '🎨',
        'database': '🗄️',
        'tools': '🔧',
        'cloud': '☁️',
        'ai': '🤖',
        'data': '📊',
        'cs': '🧠'
      };
      return emojiMap[category] || '💼';
    },
    getIconClass(category) {
      return `skill-${category}`;
    },
    isNoBackgroundSkill(skillName) {
      const noBackgroundSkills = [
        'Java', 
        'Python', 
        'Spring Boot', 
        'NLP', 
        'MongoDB', 
        'MySQL', 
        'Node.js & Express.js', 
        'HTML', 
        'CSS', 
        'JavaScript', 
        'Tailwind CSS',
        'SQL',
        'Git'
      ];
      return noBackgroundSkills.includes(skillName);
    },
    isDarkCardSkill(skillName) {
      const darkCardSkills = [
        'REST APIs',
        'Data Structures & Algorithms (OOP)',
        'System Design'
      ];
      return darkCardSkills.includes(skillName);
    },
    handleImageLoad(event) {
      console.log('Certificate image loaded successfully:', event.target.src);
    },
    handleCertificateError(event) {
      console.error('Certificate image failed to load:', event.target.src);
      // Simply hide the image without adding fallback text
      event.target.style.display = 'none';
    },
    openCertificateModal(certType) {
      this.currentCertificate = this.certificates[certType];
      this.showCertModal = true;
    },
    closeCertificateModal() {
      this.showCertModal = false;
      this.currentCertificate = null;
    }
  },
};
</script>

<style scoped>
/* Skills section styling - Performance Optimized */
#practicle_skills {
  padding: 1.5rem 0; /* Further reduced padding */
  background: transparent;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.icons-section {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  justify-items: center;
  align-items: center;
  gap: 15px;
  margin-top: 0.5rem; /* Reduced margin */
  max-width: 1000px;
  margin-left: auto;
  margin-right: auto;
}

.cards-section {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 15px; /* Reduced gap */
  margin-top: 1rem; /* Reduced margin */
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
}

.icon-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 4px;
  padding: 8px;
  cursor: pointer;
  transition: transform 0.2s ease;
}

.icon-item:hover {
  transform: translateY(-5px) scale(1.1);
}

.skill-card {
  width: 12rem;
  height: 5rem;
  background: rgba(255, 255, 255, 0.08);
  border: 1px solid rgba(255, 255, 255, 0.15);
  border-radius: 12px;
  padding: 1rem;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 4px;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.2);
  will-change: transform;
  text-align: center;
}

.skill-card.no-background {
  background: transparent;
  border: none;
  box-shadow: none;
}

.skill-card.no-background:hover {
  background: transparent;
  border: none;
  box-shadow: none;
  transform: translateY(-5px) scale(1.1);
}

.skill-card.dark-card {
  background: rgba(0, 0, 0, 0.8);
  border: 1px solid rgba(255, 255, 255, 0.2);
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.4);
}

.skill-card.dark-card:hover {
  background: rgba(0, 0, 0, 0.9);
  border-color: rgba(78, 205, 196, 0.5);
  box-shadow: 0 12px 24px rgba(78, 205, 196, 0.2);
  transform: translateY(-5px) scale(1.03);
}

.skill-card:hover {
  transform: translateY(-5px) scale(1.03);
  box-shadow: 0 12px 24px rgba(78, 205, 196, 0.15);
  border-color: rgba(78, 205, 196, 0.3);
  background: rgba(255, 255, 255, 0.12);
}

.skill-image {
  height: 48px;
  width: 48px;
  object-fit: contain;
  display: inline-block;
  vertical-align: middle;
  transition: transform 0.2s ease;
  flex-shrink: 0;
}

.skill-icon-fallback {
  display: inline-block;
  width: 48px;
  height: 48px;
  text-align: center;
  font-size: 24px;
  line-height: 48px;
  background: rgba(78, 205, 196, 0.2);
  border-radius: 50%;
  transition: transform 0.2s ease;
  flex-shrink: 0;
}

.skill-name {
  color: white;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.8);
  font-weight: 600;
  font-size: 1rem; /* Standardized font size */
  text-align: center;
  transition: color 0.2s ease;
  line-height: 1.2;
  flex: 1;
}

.skill-subtitle {
  color: rgba(255, 255, 255, 0.8);
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.8);
  font-weight: 400;
  font-size: 1rem; /* Standardized font size */
  text-align: center;
  line-height: 1.1;
  margin-top: -4px;
}

.skill-card:hover .skill-image,
.skill-card:hover .skill-icon-fallback {
  transform: scale(1.1);
}

.skill-card:hover .skill-name {
  color: #4ECDC4;
}

/* Responsive Design */
@media (max-width: 768px) {
  .icons-section {
    grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
    gap: 12px;
  }

  .cards-section {
    gap: 15px;
    margin-top: 1rem;
  }

  .skill-card {
    width: 10rem;
    height: 4rem;
    gap: 3px;
  }

  .skill-name {
    font-size: 0.8rem;
  }

  .skill-subtitle {
    font-size: 0.65rem;
  }

  .skill-image,
  .skill-icon-fallback {
    height: 40px;
    width: 40px;
  }

  .skill-icon-fallback {
    font-size: 20px;
    line-height: 40px;
  }
}

@media (max-width: 480px) {
  .icons-section {
    grid-template-columns: repeat(auto-fit, minmax(80px, 1fr));
    gap: 10px;
  }

  .cards-section {
    flex-direction: column;
    align-items: center;
    gap: 10px;
  }

  .skill-card {
    width: 8rem;
    height: 3.5rem;
    padding: 6px;
    gap: 2px;
  }

  .skill-name {
    font-size: 0.75rem;
  }

  .skill-subtitle {
    font-size: 0.6rem;
  }

  .skill-image,
  .skill-icon-fallback {
    height: 32px;
    width: 32px;
  }

  .skill-icon-fallback {
    font-size: 16px;
    line-height: 32px;
  }
}

/* Certifications Section Styles */
.certifications-section {
  margin-top: 0.5rem; /* Reduced gap from skills to certifications */
  padding: 0.5rem 0; /* Reduced padding */
  text-align: left;
}

.certifications-section .container {
  max-width: 1200px;
  margin: 0;
  padding: 0 48px; /* Half inch gap from corner (48px ≈ 0.5 inch) */
}

.certifications-grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; /* 3 certificates per row */
  gap: 1.5rem 1rem; /* Reduced gaps for better spacing */
  margin-top: 1rem; /* Reduced top margin */
  width: 100%;
  padding: 0;
  justify-items: start; /* Align items to start (left) */
  align-items: start;
}

.certification-card {
  background: transparent;
  border: none;
  border-radius: 15px;
  padding: 0;
  transition: transform 0.3s ease;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  align-items: center; /* Center align the entire card content */
  text-align: center; /* Center text alignment */
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  width: 100%;
  max-width: 350px; /* Slightly increased size for better visibility */
}

.certification-card:hover {
  transform: translateY(-3px);
}

.cert-image-container {
  width: 100%;
  margin: 0;
  border-radius: 10px;
  overflow: hidden;
  background: transparent;
  min-height: 200px; /* Slightly increased for better image display */
  display: flex;
  align-items: flex-start;
  justify-content: center; /* Center the image */
  cursor: pointer;
  transition: transform 0.2s ease;
  margin-bottom: 1rem;
}

.cert-image-container:hover {
  transform: scale(1.02);
}

.cert-image {
  width: 100%;
  height: auto;
  max-height: 180px; /* Slightly increased for better visibility */
  object-fit: contain;
  border-radius: 10px;
  align-self: center;
}

.cert-info {
  display: flex;
  flex-direction: column;
  align-items: center; /* Center align text below image */
  width: 100%;
  padding: 0;
  margin: 0;
  text-align: center; /* Center text alignment */
}

.cert-title {
  font-size: 1rem; /* Standardized font size */
  font-weight: 600;
  color: #ffffff;
  margin: 0.5rem 0 0.3rem 0;
  line-height: 1.3;
  text-align: center; /* Center title text */
  width: 100%;
  padding: 0;
}

.cert-issuer {
  font-size: 1rem; /* Standardized font size */
  color: #b0b0b0;
  font-weight: 500;
  text-align: center; /* Center issuer text */
  margin: 0;
  padding: 0;
  width: 100%;
}

/* Responsive Styles for Certifications */
@media (max-width: 768px) {
  .certifications-section .container {
    padding: 0 20px; /* Reduced padding for left alignment */
  }
  
  .certifications-grid {
    grid-template-columns: 1fr 1fr; /* 2 per row on tablets */
    gap: 2rem 1rem;
    justify-items: start; /* Left align on tablets */
  }
  
  .certification-card {
    max-width: 100%;
  }
  
  .cert-title {
    font-size: 1rem;
    text-align: center; /* Keep center alignment */
    margin: 0.5rem 0 0.3rem 0;
  }
  
  .cert-issuer {
    font-size: 0.85rem;
    text-align: center; /* Keep center alignment */
    margin: 0;
  }
}

@media (max-width: 480px) {
  .certifications-section .container {
    padding: 0 24px; /* Further reduce gap on mobile */
  }
  
  .certifications-grid {
    grid-template-columns: 1fr; /* Single column on mobile */
    gap: 2rem;
    justify-items: start; /* Left align even on mobile */
  }
  
  .certification-card {
    padding: 0;
    max-width: 100%;
    align-items: center; /* Center everything on mobile */
  }
  
  .cert-image {
    max-height: 180px;
    width: 100%;
  }
  
  .cert-image-container {
    min-height: 180px; /* Smaller on mobile */
  }
  
  .cert-title {
    font-size: 1rem;
    text-align: center;
  }
  
  .cert-issuer {
    font-size: 0.85rem;
    text-align: center;
  }
  
  .certificate-modal-overlay {
    justify-content: center;
    padding: 1rem;
  }
  
  .certificate-modal-content {
    max-width: 95%;
    max-height: 85%;
    margin-left: 0;
  }
  
  .modal-cert-image {
    max-height: 60vh;
  }
}

/* Certificate Modal Styles */
.certificate-modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  align-items: center;
  justify-content: flex-start;
  z-index: 1000;
  animation: fadeIn 0.3s ease;
  padding: 2rem;
}

.certificate-modal-content {
  position: relative;
  max-width: 60%;
  max-height: 80%;
  border-radius: 10px;
  overflow: hidden;
  animation: scaleIn 0.3s ease;
  margin-left: 5%;
}

.modal-close-btn {
  position: absolute;
  top: 15px;
  right: 15px;
  background: rgba(0, 0, 0, 0.8);
  border: 2px solid rgba(255, 255, 255, 0.9);
  border-radius: 50%;
  width: 45px;
  height: 45px;
  font-size: 24px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 10000; /* Higher z-index */
  color: #ffffff;
  font-weight: bold;
  transition: all 0.2s ease;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
}

.modal-close-btn:hover {
  background: rgba(255, 255, 255, 0.9);
  color: #333;
  transform: scale(1.1);
  border-color: rgba(0, 0, 0, 0.8);
}

.modal-cert-image {
  width: 100%;
  height: auto;
  max-width: 100%;
  max-height: 70vh;
  object-fit: contain;
  border-radius: 10px;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes scaleIn {
  from { transform: scale(0.8); opacity: 0; }
  to { transform: scale(1); opacity: 1; }
}
</style>

