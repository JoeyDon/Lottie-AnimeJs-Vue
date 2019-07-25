<template>
  <div class="line">
    <img id="icon" src="../assets/icon.png" />
    <span id="text">{{ data.text }}</span>
    <span id="rewards">{{ data.rewards }}</span>
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
  line-height: 40px;
  width: 80%;
  margin: auto;
}

#icon {
  vertical-align: middle;
}

#text {
  color: #1d1d1b;
  font-family: Muli;
  font-size: 14px;
  font-weight: 300;
  line-height: 17px;
  padding-left: 10px;
}

#rewards {
  color: #1d1d1b;
  font-family: "Pedigree-UltraBold";
  font-size: 12px;
  font-weight: 400;
  letter-spacing: 1.5px;

  float: right;
}
hr {
  background-color: #e5e9f5;
  height: 1px;
  border: 0;
  margin: 0;
  /*  default margin 8 */
}
</style>
