<template>
  <div class="loader-container">
    <img :src="loader.img" alt="">
    Loading...
  </div>
</template>

<script>

export default {
  data(){
    return {
      loader: {
        img: '../assets/img/Spinner.png',
        visibility: true
      }
    }
  }
  
}
</script>

<style lang="scss" scoped>
  .loader-container{
    width: 100px;
    aspect-ratio: 1/1;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
    color: white;
    text-transform: uppercase;
    font-weight: 700;
    text-align: center;

    img{
      filter: invert(1);
      animation: rotation 900ms linear infinite;
    }
    @keyframes rotation{
      from {transform: rotate(0deg);}
      to {transform: rotate(360deg);}
    }
  }
</style>