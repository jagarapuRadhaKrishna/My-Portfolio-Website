<template>
  <section id="about" class="about-wrapper">
    <Heading :title="'About Me'" :subtitle="'Want to know me'" />

    <!-- Professional Experience -->
    <div class="sub-section">
  <h3 class="sub-title heading-like">Professional Experience</h3>
      <div class="chips">
        <div class="experience-chip" v-for="item in experience" :key="item.role">
          <div class="chip-title">{{ item.role }}</div>
          <div class="chip-meta">{{ item.dates }}</div>
          <ul class="chip-points">
            <li v-for="(p,i) in item.points" :key="i">{{ p }}</li>
          </ul>
        </div>
      </div>
    </div>

    <!-- Education -->
    <div class="sub-section">
  <h3 class="sub-title heading-like">Education</h3>
      <div class="chips">
        <div class="education-chip" v-for="edu in education" :key="edu.institution">
          <div class="chip-title">{{ edu.institution }}</div>
          <div class="chip-meta">{{ edu.dates }}</div>
          <div class="chip-degree">{{ edu.degree }}</div>
          <div class="chip-extra" v-if="edu.coursework">Relevant Coursework: {{ edu.coursework }}</div>
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

<style scoped>
.about-wrapper { 
  padding: 1rem 0; /* Further reduced padding */
  padding-left: 48px; /* Half inch gap from corner */
  padding-right: 48px; /* Half inch gap from corner */
}
.sub-section { 
  margin-top: 1rem; /* Further reduced gap between sections */
  max-width: 760px; /* Same width as experience chips */
}
.sub-title { color:#4ECDC4; font-size:1.5rem; font-weight:700; margin:0 0 0.85rem; text-align:left; letter-spacing:1px; }
.heading-like { font-family:'Orbitron', 'Helvetica', sans-serif; text-transform:uppercase; background:linear-gradient(45deg,#ffffff,#d7d7d7); -webkit-background-clip:text; background-clip:text; -webkit-text-fill-color:transparent; color:transparent; position:relative; }
.heading-like:after { content:''; position:absolute; bottom:-6px; left:0; width:70px; height:3px; background:linear-gradient(45deg,rgba(255,255,255,0.8),rgba(255,255,255,0.4)); border-radius:2px; }

/* Experience chips */
.chips { display:grid; gap:0.6rem; max-width:760px; }
.experience-chip { background:rgba(255,255,255,0.05); border:1px solid rgba(78,205,196,.3); border-radius:12px; padding:0.75rem 0.9rem; backdrop-filter:blur(10px); transition:.25s; }
.experience-chip:hover { background:rgba(255,255,255,0.12); border-color:rgba(78,205,196,.55); }
.chip-title { font-weight:600; color:#fff; font-size:1rem; margin:0 0 0.15rem; line-height:1.2; } /* Increased font size */
.chip-meta { font-size:1rem; letter-spacing:.4px; text-transform:uppercase; color:#4ECDC4; font-weight:600; margin-bottom:0.3rem; } /* Increased font size */
.chip-points { list-style:none; padding:0; margin:0; display:flex; flex-direction:column; gap:0.3rem; }
.chip-points li { position:relative; padding-left:0.75rem; font-size:1rem; line-height:1.3; color:rgba(255,255,255,.85); } /* Increased font size */
.chip-points li:before { content:'•'; position:absolute; left:0; color:#4ECDC4; }

/* Education - same styling as experience */
.education-chip { background:rgba(255,255,255,0.05); border:1px solid rgba(78,205,196,.3); border-radius:12px; padding:0.75rem 0.9rem; backdrop-filter:blur(10px); transition:.25s; }
.education-chip:hover { background:rgba(255,255,255,0.12); border-color:rgba(78,205,196,.55); }
.chip-degree { color:rgba(255,255,255,.9); font-size:1rem; margin-top:0.35rem; line-height:1.3; }
.chip-extra { color:rgba(255,255,255,.75); font-size:1rem; margin-top:0.4rem; line-height:1.35; }

@media (max-width:650px){
  .sub-title { font-size:1.3rem; }
  .chip-points li, .chip-degree, .chip-extra { font-size:1rem; }
  .about-wrapper {
    padding-left: 20px; /* Reduced padding on mobile */
    padding-right: 20px;
  }
}
</style>
 
