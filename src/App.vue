<template>
  <div id="app">
    <div class="svgContainer">
      <div ref="lottieContainer" />
      <div class="svgMask">
        <svg
          viewBox="0 0 500 150"
          preserveAspectRatio="none"
          style="height: 100%; width: 100%;"
        >
          <path
            d="M-12.41,105.09 C201.46,229.44 347.63,-91.28 522.01,141.61 L500.00,150.00 L0.00,150.00 Z"
            style="stroke: none; fill: #FFF;"
          />
        </svg>
      </div>
    </div>
    <Subtitle1 text="Lorem ipsum dolor" />
    <RoundInfo :data="dataCircle1" />
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
import RoundInfo from "./components/RoundInfo";
import SingleLine from "./components/SingleLine";
import Subtitle1 from "./components/Subtitle1";
import Subtitle2 from "./components/Subtitle2";

import animation from "./instruction/animation.json";
import lottie from "lottie-web";

export default {
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
      ],
      dataCircle1: {
        text: "YOUR FIRST WALK",
        scores: 230
      }
    };
  },
  components: {
    SingleLine,
    Subtitle1,
    Subtitle2,
    RoundInfo
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

<style lang="scss">
@import '@/styles/index.scss';




</style>
