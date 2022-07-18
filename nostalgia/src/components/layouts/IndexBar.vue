<template>
  <v-app id="inspire">
    <v-app-bar app
      inverted-scroll
      scroll-threshold="50"
    >
        <v-toolbar-title>
            <div class="title">nostalgia</div>
        </v-toolbar-title>
        <v-toolbar-items>
            <v-btn text>
                <router-link to="/"><div class="link">Home</div></router-link>
            </v-btn>
            <v-btn text>
                <router-link to="/about" router-link-exact-active>
                    <div class="link">Profile</div>
                </router-link>
            </v-btn>
            <v-btn text>
                <a href="https://twitter.com/home">Error</a>
            </v-btn>
        </v-toolbar-items>
    </v-app-bar>
  </v-app>
</template>

<script>
  export default {
    data: () => ({
    }),
  }
</script>

<style>
a {
  text-decoration: none;
}
.title{
    padding: 10px;
}
.link{
    color: #2c3e50;
}
</style>