<template>
  <div class="popup" @click="$emit('state', false)" >
    <div class="popup-inner">
      <div class="side-left">
        <div class="side-img" v-bind:style="{backgroundImage: 'url(./img/buns/id_' + data.data.id + '.jpg)'}" />
        <div class="side-map" v-bind:style="{backgroundImage: 'url(\'https://www.netmaps.net/wp-content/uploads/2016/03/Oslo-Vector-Map.jpg\')'}" >
          <l-map :zoom=13 :center="[data.data.geo_lat,data.data.geo_long]">
            <l-tile-layer url="http://{s}.tile.osm.org/{z}/{x}/{y}.png"></l-tile-layer>
             <l-marker :lat-lng="[data.data['geo_lat'],data.data['geo_long']]"></l-marker>
          </l-map>
        </div>
      </div>
      <div class="side-right grid grid-flow-row-dense">
        <div class="side-right-top">
            <div class="text-left flex justify-center align-middle">
              <div class="rating">{{ data.data.rating }}</div>
              <div class="my-auto">
                <h1 class="text-2xl "> {{data.data.bakery}} </h1>
                <h2 class="text-lg" v-if="data.data['location_name']"> {{ data.data['location_name'] }}</h2>
              </div>
            </div>
        </div>
        <img class="w-full" src="~/static/dividerTop.svg" />
        <div class="side-right-content mx-auto">
          <div class="grid lg:grid-cols-2 grid-cols-1 gap-8 justify-around">
            <data-row label="Smell" :value="data.data.smell" :has-line-below="true" />
            <data-row label="Aesthetic" :value="data.data.aesthetic" :has-line-below="true" />
            <data-row label="Juciness" :value="data.data.juiciness" :has-line-below="true" />
            <data-row label="Fluffiness" :value="data.data.fluffiness" :has-line-below="true" />
            <data-row label="Cinnamon level" :value="data.data.cinnamon" :has-line-below="true" />
            <data-row label="Sweetness" :value="data.data.sweetness" :has-line-below="true" />
            <data-row label="Taste" :value="data.data.taste" :has-line-below="true" />
            <data-row label="Price" :value="data.data.price + ' NOK'" :has-line-below="true" />
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
    @apply w-4/5 m-auto rounded-2xl overflow-hidden flex;
  }

  .side-img, .side-map{
    border-right: 4px solid #FFF3E8;
    background-size: cover;
    background-position: center;
    width: 332px;
    height: 332px;
  }

  .side-right-content{
    @apply p-8;
  }

  .side-right{
    @apply w-full;
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
