<template>
  <div class="flex text-left w-prose">
    <slot />
    <div class="">
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
