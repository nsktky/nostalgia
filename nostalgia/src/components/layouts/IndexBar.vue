<template>
  <v-app id="inspire">
    <router-view class="router-view"/>
    <v-app-bar app>
        <!-- タイトル -->
        <v-toolbar-title class="title">
            nostalgia
        </v-toolbar-title>
        <!-- barにコンテンツのリンクを配置 -->
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
.title{
    padding: 1.5rem;
}
</style>