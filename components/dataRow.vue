<template>
  <div>
    <div class="data-block grid grid-cols-2 uppercase tracking-wider">
      <div class="attribute">
        <p>{{ label }}</p>
      </div>
      <div class="data">
        <p>{{ value }}</p>
      </div>
    </div>
    <hr v-if="hasLineBelow" />
  </div>
</template>

<script>
export default {
  name: "dataRow",
  props: {
    label: String,
    value: String,
    hasLineBelow: Boolean
  }
}
</script>

<style scoped>
hr{
  border-color: var(--bg-dark);
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
