<template>
  <section id="practicle_skills">
    <Heading :title="'Technical Skills'" :subtitle="'Explore My'" />
    <div class="container">
      <div class="skills-categories">

        <!-- Programming & Backend -->
        <div class="category-section" data-aos="fade-up" data-aos-duration="800">
          <h4 class="category-title">Programming & Backend</h4>
          <div style="display: flex; justify-content: center; flex-wrap: wrap;">
            <article
              v-for="(skill, index) in getSkillsByCategory(['backend', 'programming'])"
              :key="index"
            >
              <h3>
                <img
                  v-if="skill.hasIcon"
                  :src="`/icons/${skill.imageSrc}.${skill.extension || 'png'}`"
                  class="skill-image mr-3"
                  @error="handleImageError"
                  :alt="skill.name"
                />
                <span
                  v-else
                  class="skill-icon-fallback mr-3"
                  :class="getIconClass(skill.category)"
                >
                  {{ getIconEmoji(skill.category) }}
                </span>
                {{ skill.name }}
              </h3>
            </article>
          </div>
        </div>

        <!-- Frontend & Styling -->
        <div class="category-section" data-aos="fade-up" data-aos-duration="1000">
          <h4 class="category-title">Frontend & Styling</h4>
          <div class="d-flex justify-content-center flex-wrap">
            <article
              v-for="(skill, index) in getSkillsByCategory(['frontend'])"
              :key="index"
              data-aos="zoom-in"
              :data-aos-duration="getAosDuration(index)"
            >
              <h3>
                <img
                  v-if="skill.hasIcon"
                  :src="`/icons/${skill.imageSrc}.${skill.extension || 'png'}`"
                  class="skill-image mr-3"
                  @error="handleImageError"
                  :alt="skill.name"
                />
                <span
                  v-else
                  class="skill-icon-fallback mr-3"
                  :class="getIconClass(skill.category)"
                >
                  {{ getIconEmoji(skill.category) }}
                </span>
                {{ skill.name }}
              </h3>
            </article>
          </div>
        </div>

        <!-- Databases -->
        <div class="category-section" data-aos="fade-up" data-aos-duration="1200">
          <h4 class="category-title">Databases</h4>
          <div class="d-flex justify-content-center flex-wrap">
            <article
              v-for="(skill, index) in getSkillsByCategory(['database'])"
              :key="index"
              data-aos="zoom-in"
              :data-aos-duration="getAosDuration(index)"
            >
              <h3>
                <img
                  v-if="skill.hasIcon"
                  :src="`/icons/${skill.imageSrc}.${skill.extension || 'png'}`"
                  class="skill-image mr-3"
                  @error="handleImageError"
                  :alt="skill.name"
                />
                <span
                  v-else
                  class="skill-icon-fallback mr-3"
                  :class="getIconClass(skill.category)"
                >
                  {{ getIconEmoji(skill.category) }}
                </span>
                {{ skill.name }}
              </h3>
            </article>
          </div>
        </div>

        <!-- AI & Machine Learning -->
        <div class="category-section" data-aos="fade-up" data-aos-duration="1400">
          <h4 class="category-title">AI & Machine Learning</h4>
          <div class="d-flex justify-content-center flex-wrap">
            <article
              v-for="(skill, index) in getSkillsByCategory(['ai'])"
              :key="index"
              data-aos="zoom-in"
              :data-aos-duration="getAosDuration(index)"
            >
              <h3>
                <img
                  v-if="skill.hasIcon"
                  :src="`/icons/${skill.imageSrc}.${skill.extension || 'png'}`"
                  class="skill-image mr-3"
                  @error="handleImageError"
                  :alt="skill.name"
                />
                <span
                  v-else
                  class="skill-icon-fallback mr-3"
                  :class="getIconClass(skill.category)"
                >
                  {{ getIconEmoji(skill.category) }}
                </span>
                {{ skill.name }}
              </h3>
            </article>
          </div>
        </div>

        <!-- Data Science -->
        <div class="category-section" data-aos="fade-up" data-aos-duration="1600">
          <h4 class="category-title">Data Science</h4>
          <div class="d-flex justify-content-center flex-wrap">
            <article
              v-for="(skill, index) in getSkillsByCategory(['data'])"
              :key="index"
              data-aos="zoom-in"
              :data-aos-duration="getAosDuration(index)"
            >
              <h3>
                <img
                  v-if="skill.hasIcon"
                  :src="`/icons/${skill.imageSrc}.${skill.extension || 'png'}`"
                  class="skill-image mr-3"
                  @error="handleImageError"
                  :alt="skill.name"
                />
                <span
                  v-else
                  class="skill-icon-fallback mr-3"
                  :class="getIconClass(skill.category)"
                >
                  {{ getIconEmoji(skill.category) }}
                </span>
                {{ skill.name }}
              </h3>
            </article>
          </div>
        </div>

        <!-- Computer Science Fundamentals -->
        <div class="category-section" data-aos="fade-up" data-aos-duration="1800">
          <h4 class="category-title">Computer Science Fundamentals</h4>
          <div class="d-flex justify-content-center flex-wrap">
            <article
              v-for="(skill, index) in getSkillsByCategory(['cs'])"
              :key="index"
              data-aos="zoom-in"
              :data-aos-duration="getAosDuration(index)"
            >
              <h3>
                <img
                  v-if="skill.hasIcon"
                  :src="`/icons/${skill.imageSrc}.${skill.extension || 'png'}`"
                  class="skill-image mr-3"
                  @error="handleImageError"
                  :alt="skill.name"
                />
                <span
                  v-else
                  class="skill-icon-fallback mr-3"
                  :class="getIconClass(skill.category)"
                >
                  {{ getIconEmoji(skill.category) }}
                </span>
                {{ skill.name }}
              </h3>
            </article>
          </div>
        </div>

        <!-- Tools & APIs -->
        <div class="category-section" data-aos="fade-up" data-aos-duration="2000">
          <h4 class="category-title">Tools & APIs</h4>
          <div class="d-flex justify-content-center flex-wrap">
            <article
              v-for="(skill, index) in getSkillsByCategory(['tools'])"
              :key="index"
              data-aos="zoom-in"
              :data-aos-duration="getAosDuration(index)"
            >
              <h3>
                <img
                  v-if="skill.hasIcon"
                  :src="`/icons/${skill.imageSrc}.${skill.extension || 'png'}`"
                  class="skill-image mr-3"
                  @error="handleImageError"
                  :alt="skill.name"
                />
                <span
                  v-else
                  class="skill-icon-fallback mr-3"
                  :class="getIconClass(skill.category)"
                >
                  {{ getIconEmoji(skill.category) }}
                </span>
                {{ skill.name }}
              </h3>
            </article>
          </div>
        </div>

      </div>
    </div>
  </section>
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
        // Programming & Backend
        { name: 'Java', imageSrc: 'java', category: 'backend', hasIcon: true, extension: 'png' },
        { name: 'Spring Boot', imageSrc: 'springboot', category: 'backend', hasIcon: true, extension: 'png' },
        { name: 'Python', imageSrc: 'python', category: 'programming', hasIcon: true, extension: 'png' },
        { name: 'JavaScript', imageSrc: 'js', category: 'programming', hasIcon: true, extension: 'png' },
        { name: 'Node.js', imageSrc: 'nodejs', category: 'backend', hasIcon: true, extension: 'png' },
        { name: 'Express.js', imageSrc: 'expressjs', category: 'backend', hasIcon: true, extension: 'png' },

        // Frontend & Styling
        { name: 'HTML', imageSrc: 'html', category: 'frontend', hasIcon: true, extension: 'png' },
        { name: 'CSS', imageSrc: 'css', category: 'frontend', hasIcon: true, extension: 'png' },

        // Databases
        { name: 'MySQL', imageSrc: 'mysql', category: 'database', hasIcon: true, extension: 'png' },
        { name: 'MongoDB', imageSrc: 'mongodb', category: 'database', hasIcon: true, extension: 'png' },
        { name: 'SQL', imageSrc: 'sql', category: 'database', hasIcon: true, extension: 'png' },

        // Tools & APIs
        { name: 'REST APIs', imageSrc: 'api', category: 'tools', hasIcon: true, extension: 'png' },
        { name: 'Git', imageSrc: 'git', category: 'tools', hasIcon: true, extension: 'png' },

        // AI & Machine Learning
        { name: 'Machine Learning', imageSrc: 'python', category: 'ai', hasIcon: true, extension: 'png' },
        { name: 'Scikit-learn', imageSrc: 'python', category: 'ai', hasIcon: true, extension: 'png' },
        { name: 'NLP', imageSrc: 'nlp', category: 'ai', hasIcon: true, extension: 'svg' },
        { name: 'BERT', imageSrc: 'python', category: 'ai', hasIcon: true, extension: 'png' },
        { name: 'OpenAI API', imageSrc: 'api', category: 'ai', hasIcon: true, extension: 'png' },
        { name: 'Pandas', imageSrc: 'python', category: 'data', hasIcon: true, extension: 'png' },
        { name: 'NumPy', imageSrc: 'python', category: 'data', hasIcon: true, extension: 'png' },
        { name: 'Matplotlib', imageSrc: 'python', category: 'data', hasIcon: true, extension: 'png' },
        { name: 'Seaborn', imageSrc: 'python', category: 'data', hasIcon: true, extension: 'png' },
        { name: 'Plotly', imageSrc: 'python', category: 'data', hasIcon: true, extension: 'png' },
        { name: 'AI Agents', imageSrc: 'python', category: 'ai', hasIcon: true, extension: 'png' },
        { name: 'Workflow Automation', imageSrc: 'python', category: 'ai', hasIcon: true, extension: 'png' },

        // Computer Science Fundamentals
        { name: 'Data Structures & OOP', imageSrc: 'dsa_oop', category: 'cs', hasIcon: true, extension: 'svg' },
        { name: 'Algorithms', imageSrc: 'java', category: 'cs', hasIcon: true, extension: 'png' },
        { name: 'System Design', imageSrc: 'system_design', category: 'cs', hasIcon: true, extension: 'svg' }
      ],
    };
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
    }
  },
};
</script>

<style scoped>
/* Skills section styling for black grid design */
.skills-categories {
  margin-top: 2rem;
}

.category-section {
  margin-bottom: 3rem;
}

.category-title {
  color: #4ECDC4 !important;
  text-align: center;
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
  font-family: 'Orbitron', sans-serif;
  letter-spacing: 1px;
  text-transform: uppercase;
}

h3 {
  color: white !important;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
  font-weight: 600;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.9rem;
  text-align: center;
}

article {
  width: 14rem;
  height: 4.5rem;
  gap: 0.5rem;
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 15px;
  margin: 8px;
  padding: 12px;
  transition: all 0.3s ease;
  cursor: pointer;
  position: relative;
  overflow: hidden;
}

article::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.1), transparent);
  transition: left 0.5s ease;
}

article:hover::before {
  left: 100%;
}

article:hover {
  background: rgba(255, 255, 255, 0.15);
  transform: translateY(-5px) scale(1.05);
  box-shadow: 0 15px 30px rgba(255, 255, 255, 0.1);
  border-color: rgba(255, 255, 255, 0.4);
}

.skill-image{
  height: 25px;
  width: 25px;
  filter: brightness(1.1) contrast(1.1);
  transition: all 0.3s ease;
  margin-right: 8px !important;
}

.skill-icon-fallback {
  display: inline-block;
  width: 25px;
  height: 25px;
  text-align: center;
  font-size: 18px;
  line-height: 25px;
  transition: all 0.3s ease;
  filter: brightness(1.1) contrast(1.1);
}

article:hover .skill-image,
article:hover .skill-icon-fallback {
  filter: brightness(1.3) contrast(1.2);
  transform: scale(1.1);
}

@media (max-width: 768px) {
  article {
    width: 12rem;
    height: 4rem;
    margin: 5px;
  }

  h3 {
    font-size: 0.8rem;
  }

  .skill-image {
    height: 20px;
    width: 20px;
  }

  .category-title {
    font-size: 1.2rem;
  }
}

@media (max-width: 480px) {
  article {
    width: 10rem;
    height: 3.5rem;
  }

  h3 {
    font-size: 0.7rem;
  }
}
</style>
