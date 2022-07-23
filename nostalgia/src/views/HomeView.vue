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
// 表示するGenArtをp5.jsで作成.vue-p5を使用.
import VueP5 from "vue-p5";
export default {
  name: "p5-example",
  components: {
    "vue-p5": VueP5
  },
  // 各変数をdata内で定義
  data: () => ({
    // 各点の座標を格納するリスト
     points : [],
    //  各棒の座標を格納するリスト
     bar : [],
    //  各棒の大きさを格納するリスト
     barSize : [],
    //  棒の本数.初期値は0
     bars: 0,
  }),
  methods: {
    setup(sketch) {
      // canvasのサイズはwindow準拠.
      sketch.createCanvas(sketch.windowWidth, sketch.windowHeight);
      // 棒の数をランダムに決定
      this.bars = sketch.int(sketch.random(4, 7));
      // 背景など各種基本設定
      sketch.background(85, 0, 48);
      sketch.noiseDetail(4);
      sketch.angleMode(sketch.DEGREES);
      // 点の数を決定.tileCountによって個数が決まる.
      let tileCount = 30;
      let grid = sketch.width / tileCount;
      // 点の座標をリストに格納.
      for (let y = 0; y <= sketch.height; y += grid) {
        for (let x = 0; x <= sketch.width; x += grid) {
          // createVectorでx,y座標をベクトルとして保存.
          let p = sketch.createVector(x, y);
          this.points.push(p);
        }
      }
      // 棒の座標,大きさをリストに格納
      for (let i = 0; i < this.bars; i++) {
        let x = sketch.random(sketch.width*0.2, sketch.width*0.8);
        let y = sketch.random(sketch.height*0.2, sketch.height*0.8);
        let p = sketch.createVector(x, y);
        // 棒の大きさはwidth*0.01~width*0.1でランダムに決定.
        let size = sketch.random(sketch.width*0.01, sketch.width*0.1);
        this.bar.push(p);
        this.barSize.push(size);
      }
      // テキストを表示させるための基本設定.
      // 中央揃え.
      sketch.textAlign(sketch.CENTER, sketch.CENTER);
      // テキストサイズはwidth*0.13
      sketch.textSize(sketch.width * 0.13);
    },

    draw(sketch) {
      // 各図形の枠線を非表示.
      sketch.noStroke();
      // 各点の描写.
      for (let i = 0; i < this.points.length; i++) {
        // パーリンノイズ(noise関数)で点の動きを適度に偏らせる.
        let angle = sketch.map(
          sketch.noise(this.points[i].x * 0.001, this.points[i].y * 0.001), 0, 1, 100, 600);
          // 各点の座標を上記角度でそれぞれ移動させる.
          this.points[i].add(sketch.createVector(sketch.sin(angle), sketch.cos(angle)));
        // 各点が画面外に出た時,画面内のランダムな位置に戻す.
        if (this.points[i].x > sketch.width) this.points[i].x = sketch.random(sketch.width);
        if (this.points[i].x < 0) this.points[i].x = sketch.random(sketch.width);
        if (this.points[i].y < 0) this.points[i].y = sketch.random(sketch.height);
        if (this.points[i].y > sketch.height) this.points[i].y = sketch.random(sketch.height);

        sketch.push();
        // drawingContextを使用しグラデーションの処理.
        const gradientFill = sketch.drawingContext.createRadialGradient(
          sketch.width * 0.5,
          sketch.height * 0.5,
          sketch.width * 0.1,
          sketch.width *0.5,
          sketch.height * 0.5,
          sketch.width * 0.7
        );
        // グラデーションの段階設定.中間色(0.5)を設定し自然なグラデーションにする.
        gradientFill.addColorStop(0, sketch.color(252, 232, 225));
        gradientFill.addColorStop(0.5, sketch.color(200, 162, 142));
        gradientFill.addColorStop(1, sketch.color(178, 120, 85));
        // グラデーションを適用.
        sketch.drawingContext.fillStyle = gradientFill;
        // 点を描画.
        sketch.circle(this.points[i].x+sketch.random(5), this.points[i].y+sketch.random(5), 5);

        // テキストの描写
        sketch.noStroke();
        sketch.fill(91, 0, 37);
        sketch.textStyle(sketch.BOLD);
        // テキストを中央に配置.
        sketch.text('NOSTALGIA', sketch.width/2, sketch.height/2)
        sketch.pop();
      }
      // 各棒の描写.
      for(let i = 0; i < this.bar.length; i++) {
        // 棒の幅の最小値を決定.
        sketch.strokeWeight(sketch.min(sketch.width ,sketch.height)*0.03);
        sketch.stroke(0, 200);
        // 棒の影を描画.影はframe数(frameCount)によって長く伸びる.
        sketch.line(this.bar[i].x, this.bar[i].y,
          this.bar[i].x + this.barSize[i] * sketch.frameCount * 0.005,
          this.bar[i].y - this.barSize[i] * sketch.frameCount * 0.005);
        sketch.stroke(255);
        // 棒を描画.
        sketch.line(this.bar[i].x, this.bar[i].y,
          this.bar[i].x, this.bar[i].y - this.barSize[i]);
      }
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