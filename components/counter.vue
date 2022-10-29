<template>
  <div>
    <div class="counter" />
    <div class="description">
      <p> {{ description }} </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "counter",
  props: {
    min: Number,
    max: Number,
    description: String
  },
}
</script>

<style scoped>

  .description{
    color: var(--primary-color-light);
    @apply w-48 leading-loose mx-auto;
  }

  @property --num {
    syntax: "<integer>";
    initial-value: 0;
    inherits: false;
  }
  .counter {
    animation: counter 1.5s forwards ease-in-out;
    counter-reset: num var(--num);
    font-family: 'Playfair Display', serif;
    padding: 2rem;
    color: var(--primary-color-dark);
    @apply text-6xl;
  }

  .counter::after {
    content: counter(num);
  }

  @keyframes counter {
    from {
      --num: v-bind(min);
    }
    to {
      --num: v-bind(max);
    }
  }
</style>
