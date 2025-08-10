<template>
  <section id="heading-comp" class="container">
    <p id="skills" class="text-center mt-2">{{ subtitle }}</p>
    <h1 class="title text-center mb-3">{{ title }}</h1>
  </section>
</template>

<script>
export default {
  data() {
    return {
      activeSection: 'experience',
    };
  },
  methods: {
    setActiveSection(section) {
      this.activeSection = section;
    },
  },
  props: {
    title: {
      type: String,
      required: true,
    },
    subtitle: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
/* Heading component styling for black grid design */
#heading-comp {
  margin-top: 30px; /* Drastically reduced from 100px */
  
  h1 {
    font-family: 'Orbitron', 'Helvetica', sans-serif;
    font-weight: bold;
    color: white !important;
    text-shadow: 3px 3px 6px rgba(0, 0, 0, 0.8);
    font-size: 2.5rem;
    letter-spacing: 2px;
    text-transform: uppercase;
    background: linear-gradient(45deg, #ffffff, #e0e0e0);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    position: relative;
  }
  
  h1::after {
    content: '';
    position: absolute;
    bottom: -10px;
    left: 50%;
    transform: translateX(-50%);
    width: 80px;
    height: 3px;
    background: linear-gradient(45deg, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0.4));
    border-radius: 2px;
  }
  
  p {
    color: rgba(255, 255, 255, 0.8) !important;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
    font-size: 1.2rem;
    letter-spacing: 1px;
    text-transform: uppercase;
    font-weight: 300;
  }
}
</style>
