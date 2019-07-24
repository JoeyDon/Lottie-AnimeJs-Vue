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
  font-weight: bold;
  font-size: 12px;
  line-height: 20px;

  text-align: center;
  letter-spacing: 1.5px;
}
</style>

