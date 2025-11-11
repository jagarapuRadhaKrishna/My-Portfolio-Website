<template>
  <section id="about" class="about-modern">
    <div class="container">
      <div class="section-header" data-aos="fade-up">
        <h2 class="section-title">About Me</h2>
        <p class="section-subtitle">Passion. Code. Impact.</p>
      </div>

      <div class="about-content">
        <div class="experience-section" data-aos="fade-right">
          <div class="section-label">
            <i class="fas fa-briefcase"></i>
            <h3>Professional Journey</h3>
          </div>
          
          <div class="timeline">
            <div class="timeline-item" v-for="(item, index) in experience" :key="item.role" :data-aos-delay="100 * index" data-aos="fade-up">
              <div class="timeline-marker"></div>
              <div class="timeline-content">
                <div class="timeline-header">
                  <h4 class="timeline-title">{{ item.role }}</h4>
                  <span class="timeline-date">{{ item.dates }}</span>
                </div>
                <ul class="timeline-points">
                  <li v-for="(p,i) in item.points" :key="i">{{ p }}</li>
                </ul>
              </div>
            </div>
          </div>
        </div>

        <div class="education-section" data-aos="fade-left">
          <div class="section-label">
            <i class="fas fa-graduation-cap"></i>
            <h3>Education</h3>
          </div>
          
          <div class="education-cards">
            <div class="education-card" v-for="(edu, index) in education" :key="edu.institution" :data-aos-delay="100 * index" data-aos="zoom-in">
              <div class="education-icon">
                <i class="fas fa-university"></i>
              </div>
              <div class="education-info">
                <h4 class="education-institution">{{ edu.institution }}</h4>
                <p class="education-degree">{{ edu.degree }}</p>
                <span class="education-dates">{{ edu.dates }}</span>
                <p class="education-coursework" v-if="edu.coursework">
                  <i class="fas fa-book"></i> {{ edu.coursework }}
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Heading from './common/heading.vue';
export default {
  name: 'About',
  components: { Heading },
  data() {
    return {
      experience: [
        {
          role: 'Full Stack Web Development Intern | Internzvalley – Bangalore',
          dates: 'Jul 2025 – Present',
          points: [
            'Built responsive full‑stack features using Spring Boot (REST APIs) & Node.js services',
            'Implemented JWT authentication & secure session handling',
            'Optimized queries and data flows across MongoDB & MySQL',
            'Integrated AI tooling for automation & participated in Agile sprints'
          ]
        },
        {
          role: 'Data Science Intern | Internzvalley - Bangalore',
          dates: 'Mar 2025 – Jul 2025',
          points: [
            'Developed predictive models achieving 85%+ accuracy',
            'Performed exploratory data analysis & feature engineering in Python',
            'Created Tableau / Power BI dashboards for KPI visibility',
            'Automated data cleaning workflows & applied NLP for insights'
          ]
        },
        {
          role: 'AI & ML Intern – NLP Integration | Corizo – Bangalore',
          dates: 'May 2024 – Aug 2024',
          points: [
            'Built lightweight AI automation & classification utilities',
            'Integrated NLP components into existing app flows',
            'Preprocessed structured & unstructured data (Pandas / NumPy)'
          ]
        }
      ],
      education: [
        {
          institution: 'Anil Neerukonda Institute of Technology & Sciences',
          degree: 'Bachelor of Science in Computer Science (Data Science) | CGPA: 7.0',
          dates: 'Expected May 2026',
          coursework: 'Data Structures and Algorithms, Object-Oriented Programming, AI & ML, Data Science'
        },
        {
          institution: 'Smt. B. Seetha Polytechnic (BVRIT)',
          degree: 'Computer Engineering',
          dates: '2018 – 2022'
        }
      ]
    }
  }
}
</script>

<style scoped lang="scss">

.about-modern {
  padding: 6rem 2rem 4rem;
  background: transparent;
  position: relative;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

.section-header {
  text-align: center;
  margin-bottom: 4rem;
  
  .section-title {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 3rem;
    font-weight: 700;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 50%, #f093fb 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 1rem;
  }
  
  .section-subtitle {
    font-family: 'Inter', sans-serif;
    font-size: 1.2rem;
    color: rgba(255, 255, 255, 0.6);
    font-weight: 500;
  }
}

.about-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  
  @media (max-width: 992px) {
    grid-template-columns: 1fr;
    gap: 3rem;
  }
}

.section-label {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 2rem;
  
  i {
    font-size: 1.8rem;
    color: #667eea;
  }
  
  h3 {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 1.8rem;
    font-weight: 600;
    color: rgba(255, 255, 255, 0.9);
    margin: 0;
  }
}

.timeline {
  position: relative;
  
  &::before {
    content: '';
    position: absolute;
    left: 20px;
    top: 0;
    bottom: 0;
    width: 2px;
    background: linear-gradient(180deg, #667eea, #764ba2);
  }
}

.timeline-item {
  position: relative;
  padding-left: 60px;
  margin-bottom: 2.5rem;
  
  &:last-child {
    margin-bottom: 0;
  }
  
  .timeline-marker {
    position: absolute;
    left: 14px;
    top: 0;
    width: 14px;
    height: 14px;
    background: #667eea;
    border: 3px solid rgba(10, 10, 20, 1);
    border-radius: 50%;
    box-shadow: 0 0 20px rgba(102, 126, 234, 0.5);
  }
  
  .timeline-content {
    background: rgba(255, 255, 255, 0.05);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 16px;
    padding: 1.5rem;
    transition: all 0.3s ease;
    
    &:hover {
      background: rgba(255, 255, 255, 0.08);
      border-color: rgba(102, 126, 234, 0.3);
      transform: translateX(5px);
    }
  }
  
  .timeline-header {
    margin-bottom: 1rem;
    
    .timeline-title {
      font-family: 'Inter', sans-serif;
      font-size: 1.1rem;
      font-weight: 600;
      color: rgba(255, 255, 255, 0.95);
      margin: 0 0 0.5rem;
      line-height: 1.4;
    }
    
    .timeline-date {
      font-family: 'Inter', sans-serif;
      font-size: 0.9rem;
      color: #667eea;
      font-weight: 500;
      text-transform: uppercase;
      letter-spacing: 0.5px;
    }
  }
  
  .timeline-points {
    list-style: none;
    padding: 0;
    margin: 0;
    
    li {
      font-family: 'Inter', sans-serif;
      font-size: 0.95rem;
      color: rgba(255, 255, 255, 0.7);
      line-height: 1.6;
      padding-left: 1.5rem;
      margin-bottom: 0.5rem;
      position: relative;
      
      &::before {
        content: '▹';
        position: absolute;
        left: 0;
        color: #667eea;
        font-size: 1.2rem;
      }
      
      &:last-child {
        margin-bottom: 0;
      }
    }
  }
}

.education-cards {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.education-card {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  padding: 2rem;
  display: flex;
  gap: 1.5rem;
  align-items: flex-start;
  transition: all 0.3s ease;
  
  &:hover {
    background: rgba(255, 255, 255, 0.08);
    border-color: rgba(102, 126, 234, 0.3);
    transform: translateY(-5px);
    box-shadow: 0 10px 30px rgba(102, 126, 234, 0.2);
  }
  
  .education-icon {
    width: 60px;
    height: 60px;
    background: linear-gradient(135deg, #667eea, #764ba2);
    border-radius: 16px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
    
    i {
      font-size: 1.8rem;
      color: #fff;
    }
  }
  
  .education-info {
    flex: 1;
    
    .education-institution {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 1.3rem;
      font-weight: 600;
      color: rgba(255, 255, 255, 0.95);
      margin: 0 0 0.5rem;
    }
    
    .education-degree {
      font-family: 'Inter', sans-serif;
      font-size: 1rem;
      color: rgba(255, 255, 255, 0.8);
      margin: 0 0 0.5rem;
      line-height: 1.5;
    }
    
    .education-dates {
      font-family: 'Inter', sans-serif;
      font-size: 0.9rem;
      color: #667eea;
      font-weight: 500;
      text-transform: uppercase;
      letter-spacing: 0.5px;
    }
    
    .education-coursework {
      font-family: 'Inter', sans-serif;
      font-size: 0.9rem;
      color: rgba(255, 255, 255, 0.6);
      margin: 1rem 0 0;
      padding-top: 1rem;
      border-top: 1px solid rgba(255, 255, 255, 0.1);
      
      i {
        color: #667eea;
        margin-right: 0.5rem;
      }
    }
  }
}

@media (max-width: 768px) {
  .about-modern {
    padding: 4rem 1.5rem 3rem;
  }
  
  .section-header {
    margin-bottom: 3rem;
    
    .section-title {
      font-size: 2rem;
    }
    
    .section-subtitle {
      font-size: 1rem;
    }
  }
  
  .section-label h3 {
    font-size: 1.5rem;
  }
  
  .education-card {
    flex-direction: column;
    
    .education-icon {
      width: 50px;
      height: 50px;
      
      i {
        font-size: 1.5rem;
      }
    }
  }
}
</style>
 
