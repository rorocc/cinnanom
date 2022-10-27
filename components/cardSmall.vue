<template>
 <div class="card w-full flex">
   <div class="cardImg w-1/4" />
   <div class="w-full relative p-12 justify-between ">
     <div class="data-block grid grid-cols-2 uppercase tracking-wider">
       <div class="attribute">
         <p>Location</p>
       </div>
       <div class="data">
         <p>{{ bakery }}</p>
       </div>
     </div>

     <hr />

     <div class="data-block grid grid-cols-2 uppercase tracking-wider">
       <div class="attribute">
         <p>Price</p>
       </div>
       <div class="data">
         <p>{{ price }}</p>
       </div>
     </div>

     <hr />

     <div class="data-block grid grid-cols-2 uppercase tracking-wider">
       <div class="attribute">
         <p>Price</p>
       </div>
       <div class="data">
         <p>{{ sweetness }}</p>
       </div>
     </div>
     <img src="/cardbottom.svg" class="w-full h-auto -bottom-1/5 left-0 absolute" />
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
  .data-block{
    @apply my-2;
  }

  .attribute{
    font-weight: 400;
    color: #AD7949;
    @apply text-left;
  }

  .data{
    font-weight: 600;
    color: #724012;
    @apply text-right;
  }

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
