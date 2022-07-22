<template>
  <v-app id="inspire">
    <v-main>
      <v-container>
        <v-row justify="center" align-content="center">
          <v-col
            v-for="item in images" :key="item.src"
            sm="5"
          >
            <v-card  height="90vh">
                <v-img :src="item" height="80vh"></v-img>
                <a v-bind:href="item.link">
                    <p class="title">
                        {{ item.title }}
                    </p>
                </a>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
  export default {
      data: () => ({
      images: [
        {src: require('@/assets/images/art1.jpg'),
         title: 'フレームワーク',
         link: 'https://neort.io/art/cbd87g43p9f2v73urnfg?index=0&origin=user_profile'},
        {src: require('@/assets/images/art2.jpg'),
         title: '規定',
         link: 'https://neort.io/art/cb8k5p43p9f2v73ur4lg?index=7&origin=user_profile'},
        {src: require('@/assets/images/art3.jpg'),
         title: 'REM',
         link: 'https://neort.io/art/c6o9dl43p9f1mfrqjvpg?index=228&origin=user_profile'},
        {src: require('@/assets/images/art4.jpg'),
         title: 'mizuhiki',
         link: 'https://neort.io/art/c798mr43p9f3hsjeb0j0?index=201&origin=user_profile'},
        {src: require('@/assets/images/art5.jpg'),
         title: 'モノリス',
         link: 'https://neort.io/art/c9n9dic3p9fbkmo5o39g?index=82&origin=user_profile'},
        {src: require('@/assets/images/art6.jpg'),
         title: '歯の観戦',
         link: 'https://neort.io/art/c7qcebs3p9fclnoduot0?index=174&origin=user_profile'},
        {src: require('@/assets/images/art7.jpg'),
         title: 'タイムカプセル',
         link: 'https://neort.io/art/c8eb9sc3p9fe2d0t21f0?index=144&origin=user_profile'},
        {src: require('@/assets/images/art8.jpg'),
         title: '祖霊交信',
         link: 'https://neort.io/art/c9a1qos3p9f0i94dl9gg?index=102&origin=user_profile'},
        {src: require('@/assets/images/art9.jpg'),
         title: '還魂',
         link: 'https://neort.io/art/ca91p843p9fbkmo5s490?index=55&origin=user_profile'},
      ]
    }),
  }
</script>

<style>
.title {
    padding-top: 1.5rem;
    color: #2c3e50;
    text-align: center;

}
</style>