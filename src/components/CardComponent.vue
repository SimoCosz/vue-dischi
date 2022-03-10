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
    background-color: rgba(white, 0.1);
    width: calc((100% / 5) - 20px);
    padding: 10px;
    text-align: center;
    color: white;
    cursor: pointer;

    &:hover{
      box-shadow: 10px 10px 10px black;
      transition: 100ms ease-in-out;

      .card_author, .card_year{
        color: white;
        text-shadow: 0 0 10px gold;
        transition: 100ms ease-in-out;
      }
    }

    .card_title{
      max-width: 130px;
      font-weight: 700;
      text-transform: uppercase;
      margin: 0 auto;
      margin-top: 10px;
      margin-bottom: 20px;
    }

    .card_author, .card_year{
      color: #7E7F78;
    }
    

    figure{
      margin: 0 auto;
      img{
        aspect-ratio: 1/1;
      }
    }
  }
</style>