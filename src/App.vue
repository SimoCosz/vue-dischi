<template>
  <div id="app">
    <NavComponent />
    <!-- <LoaderComponent /> -->
    <CardListComponent />
  </div>
</template>

<script>
import NavComponent from './components/NavComponent.vue'
import CardListComponent from './components/CardListComponent.vue'
// import LoaderComponent from './components/LoaderComponent.vue'


export default {
  name: 'App',
  components: {
    NavComponent,
    CardListComponent,
    // LoaderComponent
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
  // min-height: 800px;
}
</style>
