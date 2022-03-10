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
@import './assets/scss/common.scss';


#app {
  font-family: montserrat, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #1E2D3B;
}
</style>
