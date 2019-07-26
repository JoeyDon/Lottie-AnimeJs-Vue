<template>
  <div>
    <div class="grid-container">
      <div class="item1">YOUR FIRST WALK</div>
      <div class="item2">
        <img class="icon" src="../assets/icon@2x.png" />
      </div>
      <div class="item3">Main</div>
      <div class="item4">Footer</div>
    </div>
  </div>
</template>

<script>
//import anime from 'animejs/lib/anime.es.js';

export default {
  props: {
    data: Object
  },
  mounted() {
    // anime({
    //   targets: '.line',
    //   width: '100%', // -> from '28px' to '100%',
    //   easing: 'easeInOutQuad',
    //   direction: 'alternate',
    //   loop:true
    // });
  }
};
</script>

<style>
.item1 {
  grid-area: header;
}
.item2 {
  grid-area: icon;
}
.item3 {
  grid-area: main;
}
.item4 {
  grid-area: footer;
}

.grid-container {
  grid-template-columns: 50px;
  border-radius: 44px;
  display: grid;
  grid-template-areas:
    "icon header header header header header"
    "icon main main main main main"
    "icon footer footer footer footer footer";
  grid-gap: 2px;
  background-color: #2196f3;
  padding: 10px;
}

.grid-container > div {
  background-color: rgba(255, 255, 255, 0.8);
  font-size: 10px;
}

.grid-container > .item4 {
  text-align: right;
}
</style>
