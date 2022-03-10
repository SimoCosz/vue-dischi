<template>
  <div class="card">
    <figure>
      <img :src="song.poster" alt="">
    </figure>
    <h4 class="card_title">{{song.title}}</h4>
    <p class="card_author">{{song.author}}</p>
    <p class="card_year">{{song.year}}</p>
  </div>
</template>

<script>
export default {
  props: {

    song: {
      type: Object,
      required: true,
    }
  }
}
</script>

<style lang="scss" scoped>
  .card{
    background-color: #2E3A46;
    width: calc((100% / 5) - 10px);
    padding: 10px;
    text-align: center;
    color: white;
    
    img{
      aspect-ratio: 1/1;
    }
  }
</style>