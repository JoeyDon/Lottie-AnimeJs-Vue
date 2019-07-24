<template>
  <div id="app">
    <div ref="lottieContainer"></div>

    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import animation from "./instruction/animation.json";
import lottie from "lottie-web";
//import * as bodymovin from "./lottie_light.min.js"
export default {
  name: "app",
  components: {
    HelloWorld
  },
  mounted() {
    this.anim = lottie.loadAnimation({
      container: this.$refs.lottieContainer,
      renderer: "svg",
      loop: true,
      autoplay: true,
      animationData: animation,
      rendererSettings: { viewBoxSize: "400 400 800 800" }
    });
  }
};
</script>

<style>
#lottiePlayer {
}

#app {
  width: 100%;
  height: 100%;
}
</style>
