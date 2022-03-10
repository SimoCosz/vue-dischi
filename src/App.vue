<template>
  <div id="app">
    <NavComponent />
    <CardListComponent />
  </div>
</template>

<script>
import NavComponent from './components/NavComponent.vue'
import CardListComponent from './components/CardListComponent.vue'

export default {
  name: 'App',
  components: {
    NavComponent,
    CardListComponent,
  }
}
</script>

<style lang="scss">
@import './assets/scss/common.scss';


#app {
  font-family: Montserrat;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #1E2D3B;
}
</style>
