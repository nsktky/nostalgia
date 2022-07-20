<template>
  <div class="p5">
    <vue-p5
        @setup="setup"
        @draw="draw"
    >
    </vue-p5>
  </div>
</template>

<script>
import VueP5 from "vue-p5";
export default {
  name: "p5-example",
  components: {
    "vue-p5": VueP5
  },
  data: () => ({
     points : [],
     bar : [],
     barSize : [],
     bars: 0
  }),
  methods: {
    setup(sketch) {
      sketch.createCanvas(sketch.windowWidth, sketch.windowHeight);
      this.bars = sketch.int(sketch.random(3, 6));
      sketch.background(85, 0, 48);
      sketch.noiseDetail(4);
      sketch.angleMode(sketch.DEGREES);

      let tileCount = 40;
      let grid = sketch.width / tileCount;

      for (let y = 0; y <= sketch.height; y += grid) {
        for (let x = 0; x <= sketch.width; x += grid) {
          let p = sketch.createVector(x, y);
          this.points.push(p);
        }
      }

      for (let i = 0; i < this.bars; i++) {
        let x = sketch.random(sketch.width*0.2, sketch.width*0.8);
        let y = sketch.random(sketch.height*0.2, sketch.height*0.8);
        let p = sketch.createVector(x, y);
        let size = sketch.random(sketch.width*0.01, sketch.width*0.1);
        this.bar.push(p);
        this.barSize.push(size);
      }

      sketch.textAlign(sketch.CENTER, sketch.CENTER);
      sketch.textSize(sketch.width * 0.15);
    },

    draw(sketch) {
      sketch.noStroke();
      for (let i = 0; i < this.points.length; i++) {
        let angle = sketch.map(
          sketch.noise(this.points[i].x * 0.001, this.points[i].y * 0.001), 0, 1, 100, 600);
          this.points[i].add(sketch.createVector(sketch.sin(angle), sketch.cos(angle)));

        if (this.points[i].x > sketch.width) this.points[i].x = sketch.random(sketch.width);
        if (this.points[i].x < 0) this.points[i].x = sketch.random(sketch.width);
        if (this.points[i].y < 0) this.points[i].y = sketch.random(sketch.height);
        if (this.points[i].y > sketch.height) this.points[i].y = sketch.random(sketch.height);

        sketch.push();

        const gradientFill = sketch.drawingContext.createRadialGradient(
          sketch.width * 0.5,
          sketch.height * 0.5,
          sketch.width * 0.1,
          sketch.width *0.5,
          sketch.height * 0.5,
          sketch.width * 0.7
        );
        gradientFill.addColorStop(0, sketch.color(252, 232, 225));
        gradientFill.addColorStop(0.5, sketch.color(200, 162, 142));
        gradientFill.addColorStop(1, sketch.color(178, 120, 85));
        sketch.drawingContext.fillStyle = gradientFill;

        sketch.circle(this.points[i].x+sketch.random(5), this.points[i].y+sketch.random(5), 5);

        sketch.pop();
      }

      for(let i = 0; i < this.bar.length; i++) {
        sketch.strokeWeight(sketch.min(sketch.width ,sketch.height)*0.03);
        sketch.stroke(0, 200);
        sketch.line(this.bar[i].x, this.bar[i].y,
          this.bar[i].x + this.barSize[i] * sketch.frameCount * 0.005,
          this.bar[i].y - this.barSize[i] * sketch.frameCount * 0.005);
        sketch.stroke(250);
        sketch.line(this.bar[i].x, this.bar[i].y,
          this.bar[i].x, this.bar[i].y - this.barSize[i]);
      }

      sketch.noStroke();
      sketch.fill(0);
      sketch.text('NOSTALGIA', sketch.width/2, sketch.height/2)
    },
  }
};
</script>

<style>
.p5 {
    margin: 0;
    padding: 0;
    line-height:0;
}

</style>