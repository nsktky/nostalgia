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
  }),
  computed: {
  },
  methods: {
    setup(sketch) {
      sketch.createCanvas(sketch.windowWidth, sketch.windowHeight);
      sketch.background(0);
    },
    draw(sketch) {
      sketch.push();
      sketch.translate(sketch.width/2,sketch.height/sketch.random(1,5));
      sketch.rotate(sketch.map(sketch.random(sketch.frameCount),0,1,0,360));
      sketch.stroke(207, 168, 85, 30);
      sketch.noFill();
      sketch.rect(0, 0, sketch.width*0.1, sketch.width*0.1);
      sketch.line(0, 0, sketch.width, sketch.height);
      sketch.pop();
      sketch.stroke(255);
      sketch.text('nostalgia', sketch.width/2, sketch.height/2)
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