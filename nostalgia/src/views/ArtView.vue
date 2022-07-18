<template>
  <div>
    <vue-p5
        @preload="preload"
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
    },
    draw(sketch) {
      sketch.background(this.red, this.green, this.blue);
      sketch.fill(150);
      sketch.noStroke();
      sketch.circle(sketch.width*0.5, sketch.height*0.5, sketch.width*0.5);
    },
  }
};
</script>