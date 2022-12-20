<template>
  <div class="tag" v-bind:class="[darker ? 'dark' : 'light']">
    <span>
      <slot />
    </span>
  </div>
</template>

<script>
export default {
  name: "ratingBadge",
  props: {
    darker: {
      default: false,
      type: Boolean
    }
  }
}
</script>

<style scoped>
.light{
  background-image: url("~/static/ribbon.svg");
}

.dark{
  background-image: url("~/static/ribbonDarker.svg");
}

.tag{
  color: #724012;
  font-family: 'Playfair Display', serif;
  background-position: center;
  background-size: cover;
  @apply rounded-full w-14 h-14 m-4 text-2xl proportional-nums justify-center grid;
}

.tag span{
  @apply self-center my-auto ;
}
</style>
