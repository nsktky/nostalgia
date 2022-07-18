<template>
  <div id="app">
    <IndexBar />
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.router-view {
  padding: 0;
  margin: 0;
}

a {
  font-weight: bold;
  color: #2c3e50;

  &.router-link-exact-active {
    color: #42b983;
  }
}
</style>

<script>
import IndexBar from '@/components/layouts/IndexBar'
export default {
  components: {
    IndexBar
  },
}
</script>