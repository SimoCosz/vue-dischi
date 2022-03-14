<template>
  <main class="container">
      <SelectComponent
      :genreList='genreList'
      :authorList='authorList'
      @searchGenre='setGenre'
      @searchAuthor='setAuthor'
       />
    <div class="card-wrapper">
      <CardComponent v-for="(disc, i) in filterDiscs" :key="i"
      :song='disc'
      />
    </div>
  </main>
</template>

<script>
import CardComponent from './CardComponent.vue';
import SelectComponent from './SelectComponent.vue';
import axios from 'axios';

export default {
  components: {
    CardComponent,
    SelectComponent,
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
        return genre.toLowerCase().includes(this.selectedGenre.toLowerCase()) &&
                author.toLowerCase().includes(this.selectedAuthor.toLowerCase())
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

    setGenre: function(filterGenre){
      this.selectedGenre = filterGenre
    },

    setAuthor: function(filterAuthor){
      this.selectedAuthor = filterAuthor
    },
  },

  created() {
    
    this.fetchDiscs()
    
  }
  
}
</script>

<style lang="scss" scoped>
  .container{
    position: relative;

    

    .card-wrapper{
      min-height: 100%;
      display: flex;
      flex-wrap: wrap;
      gap: 10px 20px;
      padding: 40px 0;
    }

  }

</style>