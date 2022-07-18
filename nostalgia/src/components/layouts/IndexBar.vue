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
                <router-link to="/art" router-link-exact-active>
                    <div class="link">Art</div>
                </router-link>
            </v-btn>
            <v-btn text>
                <router-link to="/profile" router-link-exact-active>
                    <div class="link">Profile</div>
                </router-link>
            </v-btn>
            <v-btn text>
                <router-link to="/contact" router-link-exact-active>
                    <div class="link">Contact</div>
                </router-link>
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