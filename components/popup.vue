<template>
  <div class="popup flex" @click="$emit('state', false)" >
    <div class="popup-inner overflow-y-scroll">
      <div class="side-left">
        <div class="side-img" v-bind:style="getOptimizedImage(data.data.id)" />
        <div class="side-map" v-bind:style="{backgroundImage: 'url(\'https://www.netmaps.net/wp-content/uploads/2016/03/Oslo-Vector-Map.jpg\')'}" >
          <l-map :zoom=13 :center="[data.data.geo_lat,data.data.geo_long]">
            <l-tile-layer url="http://{s}.tile.osm.org/{z}/{x}/{y}.png"></l-tile-layer>
             <l-marker :lat-lng="[data.data['geo_lat'],data.data['geo_long']]"></l-marker>
          </l-map>
        </div>
      </div>
      <div class="side-right relative">
        <svg class="w-6 h-6 absolute top-12 right-6" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
             viewBox="0 0 460.775 460.775" xml:space="preserve">
          <path d="M285.08,230.397L456.218,59.27c6.076-6.077,6.076-15.911,0-21.986L423.511,4.565c-2.913-2.911-6.866-4.55-10.992-4.55
            c-4.127,0-8.08,1.639-10.993,4.55l-171.138,171.14L59.25,4.565c-2.913-2.911-6.866-4.55-10.993-4.55
            c-4.126,0-8.08,1.639-10.992,4.55L4.558,37.284c-6.077,6.075-6.077,15.909,0,21.986l171.138,171.128L4.575,401.505
            c-6.074,6.077-6.074,15.911,0,21.986l32.709,32.719c2.911,2.911,6.865,4.55,10.992,4.55c4.127,0,8.08-1.639,10.994-4.55
            l171.117-171.12l171.118,171.12c2.913,2.911,6.866,4.55,10.993,4.55c4.128,0,8.081-1.639,10.992-4.55l32.709-32.719
            c6.074-6.075,6.074-15.909,0-21.986L285.08,230.397z"/>
        </svg>
        <div class="side-right-top flex">
            <div class="text-left justify-center inline-flex mt-4 ml-4">
              <div class="rating">{{ data.data.rating.toFixed(1) }}</div>
              <div class="my-auto">
                <h1 class="text-2xl "> {{data.data.bakery}} </h1>
                <h2 class="text-lg" v-if="data.data['location_name']"> {{ data.data['location_name'] }}</h2>
              </div>
            </div>
        </div>
        <img class="w-full" src="~/static/dividerTop.svg" />
        <div class="side-right-content mx-auto">
          <div class="description mb-4 leading-loose max-w-prose">
            {{ data.data.comment }}
          </div>
          <div class="grid lg:grid-cols-2 grid-cols-1 gap-8 justify-around">
            <data-row label="Smell" :value="data.data.smell" :has-line-below="true" />
            <data-row label="Aesthetic" :value="data.data.aesthetic" :has-line-below="true" />
            <data-row label="Juciness" :value="data.data.juiciness" :has-line-below="true" />
            <data-row label="Fluffiness" :value="data.data.fluffiness" :has-line-below="true" />
            <data-row label="Cinnamon level" :value="data.data.cinnamony" :has-line-below="true" />
            <data-row label="Sweetness" :value="data.data.sweetness" :has-line-below="true" />
            <data-row label="Taste" :value="data.data.taste" :has-line-below="true" />
            <data-row label="Price" :value="data.data.priceNok + ' NOK'" :has-line-below="true" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "popup",
  props: {
    data: Object
  },
  methods: {
    getOptimizedImage(id) {
      const imgUrl = this.$img('./img/buns/id_' + id + '.jpg')
      return {
        backgroundImage: `url('${imgUrl}')`
      }
    }
  }
}
</script>

<style scoped>

  h1,h2{
    @apply m-0 p-0;
  }

  h1{
    font-weight: 600;
  }

  .popup{
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    z-index: 99;
    background-color: rgba(0,0,0,0.7);
    @apply h-screen;
  }

  .popup-inner{
    background-color: var(--bg-light);
    @apply md:w-4/5 w-11/12 max-h-screen overflow-x-hidden m-auto rounded-2xl md:grid grid-rows-2 md:grid-cols-2 gap-0;
  }

  .side-img, .side-map{
    border-right: 4px solid #FFF3E8;
    background-size: cover;
    background-position: center;
    width: 332px;
    height: 332px;
  }

  .side-left{
    @apply grid md:grid-cols-none grid-cols-2;
  }

  .side-right-content{
    @apply px-8 py-4 my-auto text-left;
  }

  .side-right svg{
    fill: var(--primary-color-dark);
    @apply cursor-pointer;
  }

  .side-right{
    @apply w-full h-full;
  }

  .rating{
    background-color: #FFF3E8;
    color: #724012;
    font-family: 'Playfair Display', serif;
    @apply rounded-full p-4 w-14 h-14 m-4 text-2xl proportional-nums;
  }

  .side-right-top{
    background-color: var(--bg-dark);
  }

  .side-right-top img{
    transform: rotate(180deg);
    @apply z-0 absolute;
  }

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
</style>
