<template>
  <div>
    <header class="overflow-clip">
      <section class="head p-16 text-left">
        <div class="left-0 top-0 absolute pointer-events-none w-full h-full">
          <div class="absolute w-full h-full floatingBunsBack z-0">
            <small-bun brightness="95" class="w-16 absolute bottom-64 right-64 rotate-90" />
            <small-bun brightness="95" class="w-16 absolute top-12 left-48" />
            <small-bun brightness="95" class="w-16 absolute left-64 bottom-1/3" />
          </div>
          <div class="absolute top-0 w-full h-full floatingBunsFront z-0">
            <small-bun class="w-32 absolute top-28 right-20" />
            <small-bun class="w-24 absolute top-20 left-2/3" />
            <small-bun class="w-28 absolute top-56 left-20" />
          </div>
        </div>
        <div class="flex justify-center">
          <bun class="w-56 mx-16 logo" />
          <div class="self-center">
            <h1 class="title">cinna<span>nom</span></h1>
            <h2>Discover the world of cinnamon buns in Oslo.</h2>
          </div>
        </div>
      </section>
    </header>
    <svg class="w-full z-10" viewBox="0 0 1280 148" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M1306 0H-12L39.5 97.75L240 119L530.5 53.6562L831 10.625L1153.5 41.9688L1306 107.312V0Z" fill="#F8D5B6"/>
      <path d="M227 89.5768C72 89.5768 11.6667 37.2435 -18.5 2.57683L-27 89.5768C80.5 155.475 177.5 158.679 317 131.077C456.5 103.475 647 21.4746 895 42.9746C1143 64.4746 1332.5 131.077 1332.5 131.077L1339 64.4746C1250.5 49.9746 1182 22.9746 908 2.57686C634 -17.8209 382 89.5768 227 89.5768Z" fill="#FFF3E8"/>
    </svg>
    <section id="section-facts">
      <h1 class="gradient padding"><span>Facts about the project</span></h1>
      <div class="grid md:grid-cols-3 grid-cols-1">
        <counter :min="80" :max="141" :description="'NOKs spent on buns throughout the project'" />
        <counter :min="1" :max="rawData.length" :description="'cinnamon buns rated'" />
        <counter :min="2" :max="2" :description="'cinnanom-certified testers'" />
      </div>
    </section>

    <svg class="w-full mt-32" viewBox="0 0 1280 148" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M227 89.5768C72 89.5768 11.6667 37.2435 -18.5 2.57683L-27 89.5768C80.5 155.475 177.5 158.679 317 131.077C456.5 103.475 647 21.4746 895 42.9746C1143 64.4746 1332.5 131.077 1332.5 131.077L1339 64.4746C1250.5 49.9746 1182 22.9746 908 2.57686C634 -17.8209 382 89.5768 227 89.5768Z" fill="#FFF3E8"/>
    </svg>

    <section id="section-buns">
      <popup v-if="popupData.visible" :data="popupData" @state="(state)=>{{popupData.visible = state}}" />
      <h1 class="gradient padding"><span>Take a look at all the buns</span></h1>
      <select v-model="selected" class="mb-16 styled" @change="sortData">
        <option value="rating">Sort by <span>rating</span></option>
        <option value="price">Sort by <span>price</span></option>
      </select>
      <div class="grid lg:grid-cols-2 grid-cols-1 md:gap-8 gap-16">
        <card-small class="mx-auto bunCards opacity-0" v-for="rating in sortedData" @open="clickPopup"
                    :id="rating.id"
                    :bakery="rating.bakery"
                    :rating="rating.rating"
                    :price="rating.price"
                    :sweetness="rating.sweetness" />
      </div>
    </section>

    <svg class="w-full mt-32" viewBox="0 0 1280 148" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M227 89.5768C72 89.5768 11.6667 37.2435 -18.5 2.57683L-27 89.5768C80.5 155.475 177.5 158.679 317 131.077C456.5 103.475 647 21.4746 895 42.9746C1143 64.4746 1332.5 131.077 1332.5 131.077L1339 64.4746C1250.5 49.9746 1182 22.9746 908 2.57686C634 -17.8209 382 89.5768 227 89.5768Z" fill="#FFF3E8"/>
    </svg>

    <section id="how">
      <h1 class="gradient padding"><span>How did we rate the cinnamon buns?</span></h1>
      <div class="icon-criteria">
        <criterium :heading="'Cinnamon level over 9000'" :description="'I am a wonderful description. Did you know that cinnamon is fantastic? Yes it is.'">
          <unround-circle class="w-36 h-36">
            <svg-cinnamon />
          </unround-circle>
        </criterium>
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
import SvgCinnamon from "@/components/svg/svgCinnamon";
import UnroundCircle from "@/components/svg/unroundCircle";
import Criterium from "@/components/svg/criterium";
import SmallBun from "@/components/svg/smallBun";
export default {
  name: 'IndexPage',
  components: {SmallBun, Criterium, UnroundCircle, SvgCinnamon},
  data() {
    return {
      rawData: ratingsData,
      sortedData: null,
      popupData: {
        data: null,
        visible: false
      },
      selected: 'rating'
    }
  },
  created() {
    this.sortData();
  },
  mounted() {
    this.onScrollCards()
    this.onScrollHeaderParallax()
  },
  methods: {
    onScrollHeaderParallax(){
      this.$gsap.to(".floatingBunsBack", {
        yPercent: -25,
        ease: "none",
        scrollTrigger: {
          trigger: "#section-facts",
          // start: "top bottom", // the default values
          // end: "bottom top",
          scrub: true
        },
      });

      this.$gsap.to(".floatingBunsFront", {
        yPercent: -80,
        ease: "none",
        scrollTrigger: {
          trigger: "#section-facts",
          // start: "top bottom", // the default values
          // end: "bottom top",
          scrub: true
        },
      });

    },
    onScrollCards() {
      this.$gsap.to(
        '.bunCards',
        {
          scrollTrigger: {
              trigger: '#section-buns',
              start: 'top 60%',
              end: 'top 5',
              markers: false
            },
          opacity: 1,
          duration: 1,
          ease: "Power2.easeInOut"
        }
      )
    },
    clickPopup(id){
      this.popupData.visible = true;
      this.popupData.data = this.rawData.find((item, i)=>{
        if(item.id === id){
          return this.rawData[i]
        }
      });
    },
    sortData(){
      this.sortedData = this.rawData.sort((a, b) => {
        if(this.selected === "rating"){
          if (a.rating > b.rating) {
            return -1;
          }
        }else{
          if (a.price < b.price) {
            return -1;
          }
        }
      });
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

  h1.title{
    @apply lg:text-8xl text-6xl p-0 py-6;
  }

  h1.title span{
    color: var(--primary-color-light)
  }

  h2{
    font-family: 'Playfair Display', serif;
    color: var(--primary-color-dark);
    @apply tracking-wide lg:text-xl text-lg;
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

  select{
    appearance: none;
    -moz-appearance: none;
    -webkit-appearance: none;
    color: var(--primary-color-dark);
    background-color: var(--bg-dark);
    border: 2px solid var(--bg-lightest);
    @apply px-8 py-4 rounded-2xl uppercase tracking-wide;
  }

  .styled select{
    background-image: url('data:image/svg+xml;utf8,<!doctype html> <svg viewBox="0 0 292 98" width="292" height="98"> <path d="M 292 53.415 C 292 113.293 242.707 98.323 214.109 87.414 C 185.51 76.505 136.611 74.142 87.826 91.444 C 39.04 108.746 0 90.868 0 48.809 C 0 6.75 0 25.203 0 9.083 C 116.894 -21.432 138.958 37.294 292 6.78 L 292 53.415 Z" fill="#FFF3E8" transform="matrix(-1, 0, 0, -1, 292, 98.000042)"></path> </svg>');
    background-position: right 10px top 50%;
    background-repeat: no-repeat;
    background-size: 10px;
  }

</style>
