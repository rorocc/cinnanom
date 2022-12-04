<template>
  <div class="md:flex gap-0 grid grid-rows-2 md:text-left text-center w-prose justify-center">
    <div class="mx-auto self-center items-center">
      <slot />
    </div>
    <div class="items-center justify-center my-auto">
      <h1 class="text-xl m-0 p-0">{{ heading }}</h1>
      <p>{{ description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "criterium",
  props: {
    heading: String,
    description: String
  }
}
</script>

<style scoped>

</style>
