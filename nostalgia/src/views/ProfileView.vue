<template>
  <v-app id="inspire">
    <v-main class="grey lighten-3">
      <v-container class="container">
        <v-row>
          <v-col
            cols="10"
            sm="4"
          >
            <v-sheet
              rounded="lg"
              min-height="70vh"
              elevation="1"
            >
              <a class="twitter-timeline" data-height="70vh"
                 data-lang="ja"
                 data-dnt="true"
                 data-chrome="noheader, noscrollbar, nofooter"
                 href="https://twitter.com/ayame_takuya?ref_src=twsrc%5Etfw"
              >
              </a>
            </v-sheet>
          </v-col>

          <v-col
            cols="10"
            sm="6"
          >
            <v-sheet
              min-height="70vh"
              rounded="lg"
              elevation="1"
            >
              <v-avatar class="avatar"
                color="primary"
                size="200"
              >
                <img src="@/assets/ayame.png" alt="ayame">
              </v-avatar>
              <div class="text">
                <h1>{{ name }}</h1>
                <div class="profile">
                  <h2>Profile</h2>
                  <ul class="msg-wrapper">
                    <li v-for="item in profiles" :key="item.profile">
                      {{ item.profile }}
                    </li>
                  </ul>
                  <h2>Links</h2>
                  <ul class="msg-wrapper">
                    <a v-for="item in links" :key="item.link"
                      v-bind:href="item.link">
                      <li>{{ item.name }}</li>
                    </a>
                  </ul>
                </div>
              </div>
            </v-sheet>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    data: () => ({
      name : '@ayame_takuya',
      profiles : [
        { profile: 'GenerativeArtist' },
        { profile: 'actor/飛ぶ劇場' },
        { profile: 'Stuffed Artists' },
      ],
      links : [
        { link: 'https://www.tobugeki.com/',
          name: '飛ぶ劇場'},
        { link: 'https://neort.io/@IWD3ncMyhLhqMb7dInMwosr9Yw92',
          name: 'NEORT'},
        { link: 'https://www.youtube.com/channel/UCzjFj4kBiXPT17eUldj2YqA',
          name: 'youtube'},
        { link: 'https://twitter.com/ayame_takuya',
          name: 'twitter'},
        { link: 'https://github.com/nsktky',
          name: 'GitHub'},
      ]
    }),
    mounted() {
      setTimeout(() => {
        let tweetScript = document.createElement('script')
        tweetScript.setAttribute('src', 'https://platform.twitter.com/widgets.js')
        tweetScript.setAttribute('async', 'true')
        document.head.appendChild(tweetScript)
      }, 100)
    }
  }
</script>

<style>
.container {
  margin-top: 1rem;
}
.text {
  padding: 2rem;
}
.profile {
  padding: 2rem;
  text-align: left;
}
.profile h2 {
  margin-top: 1rem;
}
.avatar {
  margin-top: 2rem;
}
</style>