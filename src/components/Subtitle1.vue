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
  height: 18px;
  color: #1d1d1b;
  font-family: "Pedigree-UltraBold";
  font-size: 16px;
  font-weight: 400;
  line-height: 18px;
  text-align: center;
  text-transform: uppercase;
  letter-spacing: 2px;
}
</style>

