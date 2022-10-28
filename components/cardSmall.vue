<template>
 <div class="card flex">
   <div class="cardImg flex-none" >
     <div class="tag">{{ sweetness }}</div>
   </div>
   <div class="w-full relative px-8 pt-6 justify-between ">
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
         <p>Sweetness</p>
       </div>
       <div class="data">
         <p>{{ sweetness }}</p>
       </div>
     </div>
     <div class="w-full h-auto bottom-0 left-0 absolute cursor-pointer" >
       <p class="absolute left-0 right-0 bottom-1/4 readMore">Read more</p>
       <img class="w-full" src="/cardbottom.svg" />
     </div>
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

  .readMore{
    font-weight: 400;
    color: #AD7949;
    @apply uppercase tracking-wider;
  }

  .card{
    background-color: #F8D5B6;
    overflow: hidden;
    width: 532px;
    height: 232px;
    @apply rounded-2xl text-sm;
  }

  .cardImg{
    border-right: 4px solid #FFF3E8;
    background-image: url("/img/example.jpeg");
    background-size: cover;
    background-position: center;
    width: 232px;
    height: 232px;
  }

  .tag{
    background-color: #FFF3E8;
    color: #724012;
    font-family: 'Playfair Display', serif;
    @apply rounded-full p-4 w-14 h-14 m-4 text-2xl proportional-nums;
  }

</style>
