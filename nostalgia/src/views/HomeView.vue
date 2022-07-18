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
    red: 100,
    green: 100,
    blue: 100
  }),
  computed: {
  },
  methods: {
    setup(sketch) {
      sketch.createCanvas(sketch.windowWidth, sketch.windowHeight);
      sketch.background(this.red, this.green, this.blue);
    },
    draw(sketch) {
      sketch.fill(150);
      sketch.noStroke();
      sketch.circle(sketch.random(sketch.width), sketch.random(sketch.height), sketch.width*0.1);
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