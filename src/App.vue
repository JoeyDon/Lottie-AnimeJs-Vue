<template>
  <div id="app">
    <div class="svgContainer">
      <div ref="lottieContainer" />
      <div class="svgMask">
        <svg viewBox="0 0 500 150" preserveAspectRatio="none" style="height: 100%; width: 100%;">
          <path
            d="M-12.41,105.09 C201.46,229.44 347.63,-91.28 522.01,141.61 L500.00,150.00 L0.00,150.00 Z"
            style="stroke: none; fill: #FFF;"
          />
        </svg>
      </div>
    </div>
    <Subtitle1 text="Lorem ipsum dolor" />
    <RoundInfo v-for="(item,index) in dataSet1" :key="item.id" :data="dataSet1[index]" />
    <Subtitle1 text="Recent Activity" />
    <Subtitle2 text="16 July 2019" />
    <SingleLine
      v-for="(item,index) in dataSet2"
      :data="{...dataSet2[index], divider: isLastElement(index,dataSet2.length)}"
      :key="item.id"
    />
    <Subtitle2 text="15 July 2019" />
    <SingleLine
      v-for="(item,index) in dataSet3"
      :data="{...dataSet3[index], divider: isLastElement(index,dataSet3.length)}"
      :key="item.id"
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
          id: 0,
          text: "YOUR FIRST WALK",
          scores: 230,
          bonus: 0
        },
        {
          id: 1,
          text: "WALK BONUS",
          scores: 230,
          bonus: 80
        }
      ],
      dataSet2: [
        {
          id: 2,
          text: "You received gift!",
          rewards: "$10"
        },
        {
          id: 3,
          text: "You went for walkies",
          rewards: "250pts"
        }
      ],
      dataSet3: [
        {
          id: 4,
          text: "You went for walkies",
          rewards: "100pts"
        },
        {
          id: 5,
          text: "You went for walkies",
          rewards: "50pts"
        },
        {
          id: 6,
          text: "You received a donation",
          rewards: "$15"
        },
        {
          id: 7,
          text: "You went for walkies",
          rewards: "50pts"
        },
        {
          id: 8,
          text: "You received a donation",
          rewards: "$20"
        }
      ]
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
@import "@/styles/index.scss";
</style>
