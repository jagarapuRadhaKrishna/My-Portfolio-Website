<template>
  <div>
    <canvas ref="canvas" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      canvas: null,
      context: null,
      circle: [],
      mouse: {
        x: 0,
        y: 0,
      },
      radius: 5,
      color: ["#334D5C", "#45B29D", "#EFC94C", "#E27A3F", "#DF5A49"],
    };
  },
  mounted() {
    this.initCanvas();
    this.initCircles();
    this.animate();
  },
  methods: {
    initCanvas() {
      this.canvas = this.$refs.canvas;
      this.context = this.canvas.getContext("2d");
      this.canvas.width = window.innerWidth;
      this.canvas.height = window.innerHeight;

      window.addEventListener("mousemove", this.handleMouseMove);
    },
    handleMouseMove(event) {
      this.mouse.x = event.clientX;
      this.mouse.y = event.clientY;
    },
    initCircles() {
      for (let i = 0; i < 10; i++) {
        const randomX = Math.random() * (this.canvas.width - this.radius * 1) + this.radius;
        const randomY = Math.random() * (this.canvas.height - this.radius * 1) + this.radius;
        this.circle.push({
          x: randomX,
          y: randomY,
          radius: this.radius,
          color: this.color[Math.floor(Math.random() * this.color.length)],
          dx: (Math.random() - 0.9) * 2,
          dy: (Math.random() - 0.9) * 2,
        });
      }
    },
    animate() {
      this.context.fillStyle = "rgba(255, 255, 255, 0.5)";

      this.context.fillRect(0, 0, this.canvas.width, this.canvas.height);

      for (let i = 0; i < this.circle.length; i++) {
        this.updateCircle(this.circle[i]);
        this.renderCircle(this.circle[i]);
      }

      requestAnimationFrame(this.animate);
    },
    updateCircle(circle) {
      circle.x += circle.dx;
      circle.y += circle.dy;

      if (circle.x + circle.radius > this.canvas.width || circle.x - circle.radius < 0) {
        circle.dx = -circle.dx;
      }

      if (circle.y + circle.radius > this.canvas.height || circle.y - circle.radius < 0) {
        circle.dy = -circle.dy;
      }

      if (circle.x + circle.radius * 2 > this.mouse.x && this.mouse.x !== 0) {
        circle.dx -= 0.5;
      }
      if (circle.x < this.mouse.x - circle.radius * 2 && this.mouse.x !== 0) {
        circle.dx += 0.75;
      }

      if (circle.dx > 2) circle.dx -= 0.5;

      if (circle.y + circle.radius * 2 > this.mouse.y + circle.radius * 1 && this.mouse.y !== 0) {
        circle.dy -= 0.5;
      }
      if (circle.y < this.mouse.y - circle.radius * 2 && this.mouse.y !== 0) {
        circle.dy += 0.75;
      }

      if (circle.dy > 2) circle.dy -= 0.5; // Adjusted decrease
    },
    renderCircle(circle) {
      this.context.beginPath();
      this.context.arc(circle.x, circle.y, circle.radius, 0, Math.PI * 2, false);
      this.context.fillStyle = circle.color;
      this.context.strokeStyle = circle.color;
      this.context.fill();
      this.context.stroke();
    },
  },
  beforeDestroy() {
    window.removeEventListener("mousemove", this.handleMouseMove);
  },
};
</script>

<style scoped>
canvas {
  position: fixed;
  top: 0;
  left: 0;
  z-index: -1;
}
</style>
