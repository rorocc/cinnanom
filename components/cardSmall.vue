<template>
 <div class="card w-full flex">
   <div class="cardImg w-1/4" />
   <div class="w-full relative w-3/4">
     <p>{{ bakery }}</p>
     <p>{{ price }}</p>
     <p>{{ sweetness }}</p>
     <img src="/cardbottom.svg" class="w-full h-auto bottom-0 left-0 absolute" />
   </div>
 </div>
</template>

<script>
export default {
  name: "cardSmall",
  props: {
    bakery: String,
    price: Number,
    sweetness: Number
  }
}
</script>

<style scoped>
  .card{
    background-color: #F8D5B6;
    overflow: hidden;
    @apply rounded-2xl;
  }

  .cardImg{
    border-right: 2px solid #FFF3E8;
    background-image: url("/img/example.jpeg");
    background-size: cover;
    background-position: center;
    @apply w-48 h-48;
  }
</style>
