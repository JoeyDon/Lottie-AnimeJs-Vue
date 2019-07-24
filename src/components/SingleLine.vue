<template>
  <div class="line">
    <h5>
      {{ data.text }}
      <span>{{ data.rewards}}</span>
    </h5>
    <hr v-if="data.divider" />
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
.line {
  margin: auto;
  width: 80%;
}
.line h5 {
  position: relative;
}
.line h5 span {
  position: absolute;
  right: 0;
}

hr {
  background-color: #e5e9f5;
  height: 1px;
  border: 0;
}
</style>
