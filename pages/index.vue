<template>
  <div>
    <header>
      <section class="head">
        <h1>cinnanom</h1>
        <h2>Discover the world of cinnamon buns in Oslo.</h2>
      </section>
    </header>
    <svg class="w-full" viewBox="0 0 1280 148" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M1306 0H-12L39.5 97.75L240 119L530.5 53.6562L831 10.625L1153.5 41.9688L1306 107.312V0Z" fill="#F8D5B6"/>
      <path d="M227 89.5768C72 89.5768 11.6667 37.2435 -18.5 2.57683L-27 89.5768C80.5 155.475 177.5 158.679 317 131.077C456.5 103.475 647 21.4746 895 42.9746C1143 64.4746 1332.5 131.077 1332.5 131.077L1339 64.4746C1250.5 49.9746 1182 22.9746 908 2.57686C634 -17.8209 382 89.5768 227 89.5768Z" fill="#FFF3E8"/>
    </svg>
    <section>
      <h1 class="gradient padding"><span>Facts about the project</span></h1>
      <div class="grid md:grid-cols-3 grid-cols-1">
        <counter :min="80" :max="141" :description="'NOKs spent on buns throughout the project'" />
        <counter :min="1" :max="data.length" :description="'cinnamon buns rated'" />
        <counter :min="2" :max="2" :description="'cinnanom-certified testers'" />
      </div>
    </section>

    <svg class="w-full my-32" viewBox="0 0 1280 148" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M227 89.5768C72 89.5768 11.6667 37.2435 -18.5 2.57683L-27 89.5768C80.5 155.475 177.5 158.679 317 131.077C456.5 103.475 647 21.4746 895 42.9746C1143 64.4746 1332.5 131.077 1332.5 131.077L1339 64.4746C1250.5 49.9746 1182 22.9746 908 2.57686C634 -17.8209 382 89.5768 227 89.5768Z" fill="#FFF3E8"/>
    </svg>

    <section>
      <h1 class="gradient padding"><span>Take a look at all the buns</span></h1>
      <div class="grid lg:grid-cols-2 grid-cols-1 gap-4">
        <card-small class="mx-auto" v-for="rating in data"
                    :id="rating.id"
                    :bakery="rating.bakery"
                    :rating="rating.rating"
                    :price="rating.price"
                    :sweetness="rating.sweetness" />
      </div>
    </section>
    <footer>
      <svg class="w-full" viewBox="0 0 1280 136" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M224 88.6263C69.0001 88.6263 30.1667 64.1667 6.10352e-05 29.5L0 136H1280V50.5C1232.67 37.1667 1128.2 15.2263 905 1.62628C647.906 -14.0389 379 88.6263 224 88.6263Z" fill="#FFF3E8"/>
      </svg>
      <div class="w-full p-16">
        <div class="max-w-prose leading-loose">
          This is a private project completely made for fun without any commerical intentions. <br /> The ratings were done by a few private subjects without commerical interests or influence.
        </div>
      </div>
    </footer>
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

  :root{
    --primary-color-dark: #724012;
    --primary-color-light: #C8986D;
    --bg-light: #FFEAD7;
    --bg-lightest: #FFF3E8;
    --bg-dark: #F8D5B6;
  }

  * p{
    font-family: 'Inter', sans-serif;
  }

  body{
    background-color: var(--bg-light);
  }

  section{
    @apply container mx-auto text-center;
  }

  h1{
    font-family: 'Playfair Display', serif;
    color: var(--primary-color-dark);
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

  header{
    background-color: var(--bg-dark);
  }

  footer{
    @apply mt-48;
  }

  footer div{
    background-color: var(--bg-lightest);
    color: var(--primary-color-light);
  }
</style>
