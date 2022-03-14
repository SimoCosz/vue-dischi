<template>
<div>
<select @change="filterGenre" v-model="selectedGenre" name="genre" class="genre-select">
    <option value="">All</option>
    <option v-for="(genre, i) in genreList" :key="i" :value="genre">{{genre}}</option>
  </select>
  
  <select @change="filterAuthor" v-model="selectedAuthor" name="author" class="genre-select">
    <option value="">All</option>
    <option v-for="(author, i) in authorList" :key="i" :value="author">{{author}}</option>
  </select></div>
</template>

<script>
export default {
  props: {
    genreList: Array,
    authorList: Array,
  },

  data() {
    return {
      selectedGenre: '',
      selectedAuthor: '',
    }
  },

  methods:{
    filterGenre: function(){
      this.$emit("searchGenre", this.selectedGenre)
    },

    filterAuthor: function(){
      this.$emit("searchAuthor", this.selectedAuthor)
    },

  }

  
  
}
</script>

<style lang="scss" scoped>
.genre-select{
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
</style>