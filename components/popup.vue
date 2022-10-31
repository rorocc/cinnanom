<template>
  <div class="popup">
    <div class="popup-inner">
      <slot />
      <button class="popup-close">
        Close
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "popup"
}
</script>

<style scoped>
  .popup{
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    z-index: 99;
    background-color: rgba(0,0,0,0.5);
  }
</style>
