<template>
  <main class="container">
    <select v-model="selectedGenre" name="genre" id="genre-select">
      <option value="">All</option>
      <option value="Rock">Rock</option>
      <option value="Pop">Pop</option>
      <option value="Jazz">Jazz</option>
      <option value="Metal">Metal</option>
    </select>
    <div class="card-wrapper">
      <CardComponent v-for="(disc, i) in setFilter()" :key="i"
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
      selectedGenre: '',
    }
  },

  methods: {
    // loading: function(){
    //   setTimeout(this.fetchDiscs, 3000)
    // },
      fetchDiscs: function(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then(res => {
          this.discs = res.data.response
      })
    },

    setFilter: function(){
      let filteredDiscs = [];

      for (let i = 0; i < this.discs.length; i++){

        if (this.selectedGenre != ""){
          if ( this.discs[i].genre == this.selectedGenre){
            filteredDiscs.push(this.discs[i])
          }
        } else {
            filteredDiscs.push(this.discs[i])
          }
      }
      return filteredDiscs
    }
  },

  created() {
    
    this.fetchDiscs()
    
  }
  
}
</script>

<style lang="scss" scoped>
  .container{
    position: relative;

    #genre-select{
      width: 200px;
      border: none;
      background-color: rgba(white, 0.3);
      margin-right: 100px;
      margin-top: 30px;
      padding: 0 5px;
      border-radius: 4px;
      color: white;
      font-weight: 700;
    }

    .card-wrapper{
      min-height: 100%;
      display: flex;
      flex-wrap: wrap;
      gap: 10px 20px;
      padding: 40px 0;
    }

  }

</style>