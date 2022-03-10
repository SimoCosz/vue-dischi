<template>
  <div id="app">
    <NavComponent />
    <MainComponent />
  </div>
</template>

<script>
import NavComponent from './components/NavComponent.vue'
import MainComponent from './components/MainComponent.vue'


export default {
  name: 'App',
  components: {
    NavComponent,
    MainComponent,
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
