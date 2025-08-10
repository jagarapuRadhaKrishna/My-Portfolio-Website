
<template>
  <section>
    <Heading :title="'My Journey'" :subtitle="'A look at my work, achievements, and contributions'" />
    
    <div class="container gallery-div">
      <div id="gallery">
        <div>
          <img data-aos="fade-left" data-aos-duration="1000" zoomtastic src="../assets/journey/meee.jpeg" alt="profile pic" />
        </div>
        <div>
          <img data-aos="fade-left" data-aos-duration="1000" zoomtastic src="/journey/work-desk-macbook.jpg" alt="MacBook Pro Work Desk Setup" />
          <a href="#lightbox-2">My Work Desk</a>
        </div>
        <div>
          <img data-aos="fade-left" data-aos-duration="1000" zoomtastic src="../assets/journey/me2.jpg" alt="profile pic" />
        </div>
        <div>
          <img data-aos="fade-left" data-aos-duration="1000" zoomtastic src="../assets/journey/me5.jpeg" alt="profile pic" />
        </div>
        <div>
          <img data-aos="fade-left" data-aos-duration="1000" zoomtastic src="../assets/journey/me1.jpg" alt="profile pic" />
        </div>
        <div>
          <img data-aos="fade-left" data-aos-duration="1000" zoomtastic src="/journey/dell-laptop.jpeg" alt="Dell Inspiron Laptop" />
        </div>

      </div>
      
    </div>
  </section>
</template>

<script>
  import VueSlickCarousel from 'vue-slick-carousel'
  import 'vue-slick-carousel/dist/vue-slick-carousel.css'
  import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'
  import Heading from "./common/heading.vue";
 
  export default {
    components: { VueSlickCarousel, Heading },
    methods: {
      viewUrl(url) {
        window.location.href = url;
      }
    }
  }
</script>

<style scoped lang="scss">
/* Journey section styling for black grid design */
.gallery-div {
  height: 30rem;
  overflow: hidden;
}

#gallery {
  display: grid;
  height: calc(100vh - 10px);
  grid-template: repeat(6, 1fr)/repeat(6, 1fr);
  grid-gap: 0.5em;
}

@media (max-width: 800px) {
  #gallery {
    display: flex;
    align-items: flex-start;
    flex-wrap: wrap;
    justify-content: center;
  }
  #gallery > div {
    width: 48%;
    margin: 1%;
  }
}

@media (max-width: 800px) and (max-width: 350px) {
  #gallery > div {
    width: 98%;
  }
}

#gallery > div:nth-child(6n+1) {
  grid-column: span 2;
  grid-row: span 2;
}

#gallery > div:nth-child(2) {
  grid-column: span 3;
  grid-row: span 3;
}

#gallery > div:nth-child(4) {
  grid-column: span 1;
  grid-row: span 2;
}

#gallery > div > a {
  opacity: 0;
  position: absolute;
  color: white !important;
  background: rgba(0, 0, 0, 0.7);
  backdrop-filter: blur(10px);
  font: bold 2em "Orbitron", "Helvetica";
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
  padding: 1rem; /* Reduced padding */
  width: 100%;
  height: 100%;
  transition: all ease 0.5s;
  border: 1px solid rgba(255, 255, 255, 0.2);
}

#gallery > div > img {
  width: 100%;
  min-height: 100%;
  transition: all ease 0.5s;
  filter: brightness(0.8);
}

#gallery > div:hover img {
  filter: blur(4px) brightness(1.1);
  transform: scale(1.05);
}

#gallery > div:hover a {
  opacity: 1;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(15px);
}

#gallery > div {
  overflow: hidden;
  position: relative;
  box-shadow: 0 10px 30px rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 10px;
  transition: all 0.3s ease;
}

#gallery > div:hover {
  transform: translateY(-5px);
  box-shadow: 0 15px 40px rgba(255, 255, 255, 0.2);
  border-color: rgba(255, 255, 255, 0.4);
}

#gallery div,
#gallery a {
  display: flex;
  justify-content: center;
  align-items: center;
  text-decoration: none;
}

[id^=lightbox-] {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.8);
  backdrop-filter: blur(10px);
  display: flex;
  opacity: 0;
  transition: opacity 450ms ease-in-out;
  align-items: center;
  justify-content: center;
  pointer-events: none;
}

[id^=lightbox-]:target {
  opacity: 1;
  pointer-events: inherit;
}

[id^=lightbox-]:target img {
  filter: blur(0);
}

[id^=lightbox-] .content {
  max-width: 90%;
  position: relative;
  color: #fff;
  border: 1px solid rgba(255, 255, 255, 0.3);
  border-radius: 15px;
  overflow: hidden;
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(20px);
}

[id^=lightbox-] .content:hover > a.close {
  opacity: 1;
  transform: scale(1, 1);
}

[id^=lightbox-] .content:hover > .title {
  opacity: 1;
  transform: translateY(-3px);
}

[id^=lightbox-] .content:hover > .title::after {
  opacity: 1;
}

[id^=lightbox-] .content > * {
  transition: all 450ms ease-in-out;
}

[id^=lightbox-] .title {
  display: block;
  margin: 0;
  padding: 1em;
  position: absolute;
  bottom: 0;
  width: 100%;
  transform: translateY(50%);
  font-size: 1.5em;
  opacity: 0;
  color: white !important;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
}

[id^=lightbox-] .title::after {
  content: " ";
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  bottom: 0;
  left: 0;
  height: 100%;
  width: 100%;
  position: absolute;
  transition: all 350ms ease-in-out 250ms;
  opacity: 0;
  transform-origin: bottom;
  mix-blend-mode: soft-light;
}

[id^=lightbox-] img {
  max-height: 90vh;
  max-width: 100%;
  margin: 0;
  padding: 0;
  filter: blur(50px);
  border-radius: 10px;
}

[id^=lightbox-] a.close {
  width: 2em;
  height: 2em;
  position: absolute;
  right: 0;
  top: 0;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.3);
  border-radius: 0 15px 0 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  transform: scale(0, 0);
  opacity: 0;
  transform-origin: right top;
  text-decoration: none;
  color: white !important;
  transition: all 0.3s ease;
}

[id^=lightbox-] a.close:hover {
  background: rgba(255, 255, 255, 0.2);
  transform: scale(1.1, 1.1);
}

[id^=lightbox-] a.close::after {
  content: "✕";
  font-weight: bold;
}
</style>


