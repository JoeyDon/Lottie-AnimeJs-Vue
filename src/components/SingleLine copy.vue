<template>
  <div class="line">
    <h5>
      <svg
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          fill-rule="evenodd"
          clip-rule="evenodd"
          d="M12 24C18.6274 24 24 18.6274 24 12C24 5.37258 18.6274 0 12 0C5.37258 0 0 5.37258 0 12C0 18.6274 5.37258 24 12 24Z"
          fill="#FFC20E"
        />
      </svg>
      <span class="text">{{ data.text }}</span>
      <span class="rewards">{{ data.rewards }}</span>
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
.line h5 .rewards {
  position: absolute;
  right: 0;
}

hr {
  background-color: #e5e9f5;
  height: 1px;
  border: 0;
}
</style>
