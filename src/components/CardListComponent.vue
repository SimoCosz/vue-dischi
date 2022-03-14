<template>
  <main class="container">
    <select v-model="selectedGenre" name="genre" id="genre-select">
      <option value="">All</option>
      <option v-for="(genre, i) in genreList" :key="i" :value="genre">{{genre}}</option>
    </select>
    <select v-model="selectedAuthor" name="author" id="genre-select">
      <option value="">All</option>
      <option v-for="(author, i) in authorList" :key="i" :value="author">{{author}}</option>
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
      selectedAuthor: '',
      genreList: [],
      authorList: [],
    }
  },

  computed: {
    filterDiscs: function(){
      return this.discs.filter(el => {
        const {genre, author} = el
        return genre.toLowerCase().includes(this.genrelist.toLowerCase()) &&
        author.toLowerCase().includes(this.authorList.toLowerCase())
      })
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
          this.genreFilter(this.discs)
          this.authorFilter(this.discs)
      })
    },

    authorFilter: function(discs){
      discs.forEach((el) => {
        if(!this.authorList.includes(el.author)){
          this.authorList.push(el.author)
        }
      });
    },

    genreFilter: function(discs){
      discs.forEach((el) => {
        if(!this.genreList.includes(el.genre)){
          this.genreList.push(el.genre)
        }
      });
    },

    setFilter: function(){
      let filteredDiscs = [];

      for (let i = 0; i < this.discs.length; i++){

        if (this.selectedGenre != "" || this.selectedAuthor != ""){
          if ( this.discs[i].genre == this.selectedGenre || this.discs[i].author == this.selectedAuthor){
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