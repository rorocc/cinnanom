<template>
  <div class="relative items-center">
    <svg class="bg" viewBox="0 0 400 400" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M393.828 161.114C412.134 240.945 390.859 270.611 314.667 348.292C238.474 425.973 178.768 402.839 98.457 365.006C44.5283 339.601 0 260.806 0 205.406C0 154.159 10.5515 106.696 45.3512 71.0963C80.1509 35.4962 166.734 -20.1226 254.801 7.38637C342.868 34.8954 375.522 81.2834 393.828 161.114Z" fill="#FFF3E8"/>
    </svg>
    <div class="slot">
      <slot />
    </div>
  </div>
</template>

<script>
export default {
  name: "unroundCircle",
  methods: {
    getRandomRotation(){
      let rand = Math.floor(Math.random() * 360);
      console.log("random", rand)
      return rand;
    }
  }
}
</script>

<style scoped>
  .bg svg{
    @apply absolute z-0;
  }

  .slot svg{
    @apply w-2/3 absolute left-0 right-0 bottom-1/3 left-1/4;
  }
</style>
