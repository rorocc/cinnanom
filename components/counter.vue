<template>
  <div class="relative content-center">
    <div class="relative z-10">
      <div class="counter" />
      <div class="description">
        <p> {{ description }} </p>
      </div>
    </div>
    <svg class="absolute w-48" viewBox="0 0 400 400" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M393.828 161.114C412.134 240.945 390.859 270.611 314.667 348.292C238.474 425.973 178.768 402.839 98.457 365.006C44.5283 339.601 0 260.806 0 205.406C0 154.159 10.5515 106.696 45.3512 71.0963C80.1509 35.4962 166.734 -20.1226 254.801 7.38637C342.868 34.8954 375.522 81.2834 393.828 161.114Z" fill="#FFF3E8"/>
    </svg>
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
