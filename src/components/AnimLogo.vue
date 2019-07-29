<template>
  <div class="svgContainer">
    <div ref="lottieContainer" />
    <div class="svgMask">
      <svg viewBox="0 0 500 150"
preserveAspectRatio="none">
        <path
          d="M-12.41,105.09 C201.46,229.44 347.63,-91.28 522.01,141.61 L500.00,150.00 L0.00,150.00 Z"
          style="stroke: none; fill: #FFF;"
        />
      </svg>
    </div>
  </div>
</template>

<script>
import animation from "../instruction/animation.json";
import lottie from "lottie-web";

export default {
  props: {
    text: String
  },
  data: function() {
    return {
      screenWidth: 0,
      animInstance: null
    };
  },
  mounted() {
    this.screenWidth = window.screen.width;
    this.renderAnimationSVG();

    // watch screen orientation
    window.onorientationchange = () => {
      // Destroy the old width instance
      this.animInstance.destroy();
      // Re-read the new width after rotating
      this.screenWidth = window.screen.width;
      console.log(
        "the orientation of the device is now " + screen.orientation.angle
      );
      console.log(`New screen width is ${this.screenWidth}`);

      // Re-render the SVG animation
      this.renderAnimationSVG();
    };
  },

  methods: {
    renderAnimationSVG() {
      this.animInstance = lottie.loadAnimation({
        container: this.$refs.lottieContainer,
        renderer: "svg",
        loop: true,
        autoplay: true,
        animationData: animation,
        rendererSettings: this.setViewBoxSize(this.screenWidth)
      });
    },
    /*
    For mobile phones: 
    rendererSettings: { viewBoxSize: "400 400 800 800" }

    Ipad: 768*1024
    rendererSettings: { viewBoxSize: "200 550 1200 1200" }

    IpadPro: 1024*1366
    rendererSettings: { viewBoxSize: "200 550 1200 1200" }

    IpadProLandscape: 1366*1024
    rendererSettings: { viewBoxSize: "200 550 1200 1200" }
  */
    setViewBoxSize(width) {
      if (width < 768) {
        return { viewBoxSize: "400 400 800 800" };
      }
      if (width >= 768 && width < 1024) {
        return { viewBoxSize: "200 550 1200 1200" };
      }
      if (width >= 1024 && width < 1366) {
        return { viewBoxSize: "100 550 1400 1400" };
      }
      if (width >= 1366) {
        return { viewBoxSize: "-100 550 1800 1800" };
      }
    }
  }
};
</script>

<style scoped>
</style>

