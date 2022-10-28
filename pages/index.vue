<template>
  <div>
    <section class="head">
      <h1>cinnanom</h1>
      <h2>Discover the world of cinnamon buns in Oslo.</h2>
    </section>
    <img src="/divider.svg" class="w-full">
    <section>
      <h1 class="gradient padding"><span>The greatest bun</span></h1>
    </section>
    <img src="/divider.svg" class="w-full">
    <section>
      <h1 class="gradient padding"><span>Take a look at all the buns</span></h1>
      <div class="grid lg:grid-cols-2 grid-cols-1 space-y-4 justify-around">
        <card-small v-for="rating in data"
                    :bakery="rating.bakery"
                    :price="rating.price"
                    :sweetness="rating.sweetness" />
      </div>
    </section>
  </div>
</template>

<script>
import ratingsData from "../static/data.json"
export default {
  name: 'IndexPage',
  data() {
    return {
      data: ratingsData
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap');

  * p{
    font-family: 'Inter', sans-serif;
  }

  body{
    background-color: #FFEAD7;
  }

  section{
    @apply container mx-auto text-center;
  }

  h1{
    font-family: 'Playfair Display', serif;
    color: #724012;
    @apply text-4xl p-16;
  }

  h1.gradient span{
    background: linear-gradient(0deg, rgba(255,0,255,0) 0%, rgba(255,0,255,0) 16%, rgb(248, 213, 182) 16%, rgb(248, 213, 182) 41%, rgba(255,0,255,0) 41%);
  }

  h1.padding span{
    padding: 0.5em 0.2em 0.5em 0.2em;
    box-decoration-break: clone;
    -webkit-box-decoration-break: clone;
  }

  .head{
    background-color: #F8D5B6;
  }
</style>
