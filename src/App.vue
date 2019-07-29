<template>
  <div id="app">
    <AnimiLogo />
    <Subtitle1 text="Lorem ipsum dolor" />
    <RoundInfo
      v-for="(item,index) in dataSet1"
      :key="item.id"
      :data="dataSet1[index]"
    />
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
import AnimiLogo from "./components/AnimLogo";
import RoundInfo from "./components/RoundInfo";
import SingleLine from "./components/SingleLine";
import Subtitle1 from "./components/Subtitle1";
import Subtitle2 from "./components/Subtitle2";
import dataFromAPI from "./data.json";

export default {
  data: function() {
    return { ...dataFromAPI };
  },
  components: {
    AnimiLogo,
    SingleLine,
    Subtitle1,
    Subtitle2,
    RoundInfo
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
