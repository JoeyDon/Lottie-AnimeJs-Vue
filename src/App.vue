<template>
  <div id="app">
    <div style="height: 500px; overflow: hidden;">
      <div
        ref="lottieContainer"
      />
      <div class="mask">
        <svg
          viewBox="0 0 500 150"
          preserveAspectRatio="none"
          style="height: 100%; width: 100%;"
        ><path
          d="M-12.41,105.09 C201.46,229.44 347.63,-91.28 522.01,141.61 L500.00,150.00 L0.00,150.00 Z"
          style="stroke: none; fill: #FFF;"
        /></svg>
      </div>
    </div>
   
    <Subtitle1 text="Recent Activity" />
    <Subtitle2 text="16 July 2019" />
    <SingleLine
      v-for="(item,index) in dataSet1"
      :data="{...dataSet1[index], divider: isLastElement(index,dataSet1.length)}"
      :key="index"
    />
    <Subtitle2 text="15 July 2019" />
    <SingleLine
      v-for="(item,index) in dataSet2"
      :data="{...dataSet2[index], divider: isLastElement(index,dataSet2.length)}"
      :key="index"
    />
  </div>
</template>

<script>
import SingleLine from "./components/SingleLine";
import Subtitle1 from "./components/Subtitle1";
import Subtitle2 from "./components/Subtitle2";
import animation from "./instruction/animation.json";
import lottie from "lottie-web";

export default {
  name: "App",
  data: function() {
    return {
      dataSet1: [
        {
          text: "You received gift!",
          rewards: "$10"
        },
        {
          text: "You went for walkies",
          rewards: "250pts"
        }
      ],
      dataSet2: [
        {
          text: "You went for walkies",
          rewards: "100pts"
        },
        {
          text: "You went for walkies",
          rewards: "50pts"
        },
        {
          text: "You received a donation",
          rewards: "$15"
        },
        {
          text: "You went for walkies",
          rewards: "50pts"
        },
        {
          text: "You received a donation",
          rewards: "$20"
        }
      ]
    };
  },
  components: {
    SingleLine,
    Subtitle1,
    Subtitle2
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
  },
  methods: {
    isLastElement(index, arrLength) {
      return index !== arrLength - 1;
    }
  }
  /*
  todo:
  1. computed date today yesterday
  */
};
</script>

<style>
#app {
  width: 100%;
  height: 100%;
}

.mask{
  position: absolute;
  top: 200px;
  left: 0;
  width: 100%
}

/* .wave {
  position: relative;
  background: linear-gradient(90deg,#f0027f,#75489f);
  min-height: 600px;
}

.wave:before{
  content:'';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 150px;
  background: url('./assets/wave.png');
  background-size: cover
} */

</style>
