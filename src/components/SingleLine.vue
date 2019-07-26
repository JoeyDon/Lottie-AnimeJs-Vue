<template>
  <div class="singleLine">
    <img
      class="icon"
      src="../assets/icon.png"
    >
    <span class="text">{{ data.text }}</span>
    <span class="rewards">{{ data.rewards }}</span>
    <hr v-if="data.divider">
  </div>
</template>

<script>
export default {
  props: {
    data: Object
  }
};
</script>

<style scoped>

</style>
