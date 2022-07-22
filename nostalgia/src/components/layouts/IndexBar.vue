<template>
  <v-app id="inspire">
    <router-view class="router-view"/>
    <v-app-bar app>
        <v-toolbar-title>
            <div class="title">nostalgia</div>
        </v-toolbar-title>
        <v-toolbar-items>
            <v-btn text to="/" router-link-exact-active>
                <div class="link">Home</div>
            </v-btn>
            <v-btn text to="/art" router-link-exact-active>
                <div class="link">Art</div>
            </v-btn>
            <v-btn text to="/profile" router-link-exact-active>
                <div class="link">Profile</div>
            </v-btn>
            <v-btn text to="/contact" router-link-exact-active>
                <div class="link">Contact</div>
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
    padding: 1.5rem;
}
.link{
    color: #2c3e50;
}
</style>