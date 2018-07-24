<template>
  <canvas class="canvas"></canvas>
</template>

<script>
// const FPS = 60;
// const SCREEN_WIDTH = window.innerWidth;
// const SCREEN_HEIGHT = window.innerHeight;
// const GRAVITY = 0.4;

// let ctx;
// let particleList = [];
// let mx = null;
// let my = null;

// const init = function() {

//   ctx = canvas.getContext("2d");

//   canvas.addEventListener("mousemove", updateMousePos, false);
//   canvas.addEventListener("mouseout", resetMousePos, false);

//   loop();
// };

// var updateMousePos = function(e) {
//   var rect = e.target.getBoundingClientRect();
//   mx = e.clientX - rect.left;
//   my = e.clientY - rect.top;
// };

// var resetMousePos = function(e) {
//   mx = null;
//   my = null;
// };

// var loop = function() {
//   add();
//   update();
//   draw();
//   setTimeout(loop, 1000 / FPS);
// };

// var add = function() {
//   if (mx !== null && my !== null) {
//     var p = new Particle(mx, my);
//     p.create();

//     particleList.push(p);
//   }
// };

// var update = function() {
//   var list = [];
//   for (var i = 0; i < particleList.length; i++) {
//     particleList[i].update();

//     if (!particleList[i].isRemove) {
//       list.push(particleList[i]);
//     }
//   }
//   particleList = list;
// };

// var draw = function() {
//   ctx.fillStyle = "rgb(0, 0, 0)";
//   ctx.fillRect(0, 0, SCREEN_WIDTH, SCREEN_HEIGHT);

//   ctx.save();
//   ctx.globalCompositeOperation = "lighter";
//   for (var i = 0; i < particleList.length; i++) {
//     particleList[i].draw();
//   }
//   ctx.restore();
// };

// class Particle {
//   constructor(x, y) {
//     this.x = x;
//     this.y = y;
//     this.vx = 0;
//     this.vy = 0;
//     this.radius = 0;
//     this.color = null;
//     this.isRemove = false;
//   }

//   create() {
//     this.vx = Math.random() * 6 - 3;
//     this.vy = Math.random() * -6 - 2;
//     this.radius = Math.random() * 20 + 5;
//     var r = 150;
//     var g = Math.floor(Math.random() * 100 + 155);
//     var b = Math.floor(Math.random() * 155 + 100);
//     this.color = "rgb(" + r + "," + g + ", " + b + ")";
//   }

//   update() {
//     this.vy += GRAVITY;
//     this.x += this.vx;
//     this.y += this.vy;
//     this.radius *= 0.97;
//     if (this.x < 0 || this.x > SCREEN_WIDTH || this.y > SCREEN_HEIGHT) {
//       this.isRemove = true;
//     }
//   }

//   draw() {
//     ctx.fillStyle = this.color;
//     ctx.beginPath();
//     ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2, false);
//     ctx.fill();
//   }
// }

export default {
  data: {},
  props: {
    amount: {
      type: Number,
      default: 50
    }
  },
  watch: {
    amount() {
      this.draw(this.amount);
    }
  },
  methods: {
    draw(amount) {
      this.ctx.beginPath();
      this.ctx.clearRect(0, 0, 200, 200);
      this.ctx.arc(100, 100, amount, 0, Math.PI * 2);
      this.ctx.fill();
    }
  },
  mounted() {
    console.log(this.$el);
    this.ctx = this.$el.getContext("2d");

    this.draw(this.amount);
  }
};
</script>

<style scoped>
.canvas {
  border: 1px solid #f00;
}
</style>
