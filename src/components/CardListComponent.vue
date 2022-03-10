<template>
  <main class="container">
    <div class="card-wrapper">
      <CardComponent v-for="(disc, i) in discs" :key="i"
      :song='disc'
      />
    </div>
  </main>
</template>

<script>
import CardComponent from './CardComponent.vue'
import axios from 'axios';

export default {
  components: {
    CardComponent,
  },
  data() {
    return {
      discs: [],
    }
  },

  methods: {
    fetchDiscs: function(){
      
      axios.get('https://flynn.boolean.careers/exercises/api/array/music')
      .then(res => {
        console.log(res.data.response)
        this.discs = res.data.response
    })

    }
  },

  created() {
    
    this.fetchDiscs()
    
  }
  
}
</script>

<style lang="scss" scoped>
  .card-wrapper{
    height: max-content;
    display: flex;
    flex-wrap: wrap;
    gap: 10px 20px;
    padding: 40px;
  }
</style>