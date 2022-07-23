<template>
  <v-app id="inspire">
    <v-main class="grey lighten-3">
      <v-container class="container">
        <v-row justify="center" align-content="center">
          <v-col sm="8">
            <v-card  height="80vh" rounded>
                <!-- googleフォームを埋め込み.幅,高さを100%に設定 -->
                <iframe src="https://docs.google.com/forms/d/e/1FAIpQLSelZPOladVnrM6zbTRUoakFWNGa3M5HTQ1-WGS_a60QLVZr3g/viewform?embedded=true"
                 width="100%" height="100%" frameborder="0" marginheight="0" marginwidth="0">読み込んでいます…</iframe>
            </v-card>
           </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<style>
.container {
    padding-top: 2rem;
}
</style>