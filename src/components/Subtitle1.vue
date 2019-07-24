<template>
  <div class="line">{{ text }}</div>
</template>

<script>
export default {
  props: {
    text: String
  }
};
</script>

<style scoped>
.line {
  text-align: center;
  letter-spacing: 2px;
  text-transform: uppercase;
  font-style: normal;
  font-weight: bold;
  font-size: 16px;
}
</style>

