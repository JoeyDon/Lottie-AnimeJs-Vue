<template>
  <div>
    <div class="grid-container">
      <div class="item1">
        {{ data.text }}
      </div>
      <div class="item2">
        <img
          class="icon2x"
          ref="icon2x"
          src="../assets/icon@2x.png"
        >
      </div>
      <div class="item3">
        <div class="progressContainer">
          <div
            class="progress"
            ref="progress" 
          />
          <div
            class="progressBonus"
            ref="progressBonus"
          />
        </div>
      </div>
      <div class="item4">
        <!-- <span class="figure" ref="figure">+{{data.scores + data.bonus}}</span> -->
        +
        <span
          class="figure"
          ref="figure"
        >0</span>
      </div>
    </div>
  </div>
</template>

<script>
import anime from "animejs/lib/anime.es.js";

export default {
  props: {
    data: Object
  },
  data: function() {
    return {
      // Vinilla bar animation
      MAX_SCORE: 400,
      initialStoppedAt: 0
    };
  },
  mounted() {
    /*
      Animation 1: Scores goes up (+230).
    */
    // Create animation timeline of Anime.js
    var timeLine = anime.timeline({
      easing: "easeInOutExpo",
      duration: 1300
    });
    timeLine
      // Stage 1 for base scores (yellow color)
      .add({
        targets: this.$refs.figure,
        innerHTML: [0, this.data.scores],
        round: 1,
        delay: 1500,
        duration: 3000,
      })
      // Stage 1 for bonus scores (pink color)
      .add({
        targets: this.$refs.figure,
        innerHTML: [this.data.scores, this.data.scores + this.data.bonus],
        round: 1,
        delay: 100,
        duration: 3000,
      });

    /*
      Animation 2: Ball shaking dynamically based on bonus.
    */
    const xMax = this.data.bonus;
    var bounceTransiton = [];
    const bounceTimes = 30;

    // Define how many times it should bounce.
    // Format {value: Number} is required by the Anime.js Library.
    for(var i =0; i<bounceTimes;i++){
      if( i != (bounceTimes-1)){
        bounceTransiton.push( i%2 === 0? {value: xMax / -4} :  {value: xMax / 4})
      }
      else{
        bounceTransiton.push({value:0})
      }
    }
  
    anime({
      targets: this.$refs.icon2x,
      easing: "linear",
      delay: 5200,
      duration: 2200,

      translateX: bounceTransiton
    });


    /*
      Animation 3: Fill the bar with yellow/pink
    */
    // Move the yellow base bar first
    setTimeout(() => {
      this.move("Initial");
    }, 1500);

    // Move the pink bonus after
    setTimeout(() => {
      this.move("Bonus");
    }, 5000);
  },
  methods: {
    /*
      Function for
      Animation 3: Fill the bar with yellow/pink
    */
    move(type) {
      if (type === "Initial") {
        var elem = this.$refs.progress;
        var width = 1;
        var runAnimation = setInterval(animation, 30);
        var stopAt = (this.data.scores / this.MAX_SCORE) * 100;
        this.initialStoppedAt = stopAt;
      }
      if (type === "Bonus") {
        var elem = this.$refs.progressBonus;
        var width = this.initialStoppedAt;
        var runAnimation = setInterval(animation, 100);
        var stopAt =
          ((this.data.scores + this.data.bonus) / this.MAX_SCORE) * 100;
      }

      function animation() {
        if (width >= stopAt) {
          clearInterval(runAnimation);
        } else {
          width++;
          elem.style.width = width + "%";
        }
      }
    }
  }
};
</script>

<style>
</style>
