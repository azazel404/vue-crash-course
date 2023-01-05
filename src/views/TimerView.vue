<template>
  <div class="timer">
    <h1>This is an Timer page guys</h1>
    <div>
     <button @click="startGame" :disabled="isPlaying">play</button>
     <!-- component for processing the game -->
     <Block :delay="isDelay" v-if="isPlaying" @endThisGame="endGame" />
     <Result :score='score' v-if="showResult" />
   </div>
  </div>
</template>

<script>
import Block from "@/components/Timer/Block.vue";
import Result from "@/components/Timer/Result.vue";

export default {
  name: "TimerView",
  components: {
    Block,
    Result
  },
  data() {
    return {
        isPlaying: false,
        isDelay : null,
        score : null,
        showResult: false
    };
  },
  methods : {
    startGame() {
        // set TimeOut
        this.isDelay = 2000 + Math.random() * 5000;
        this.isPlaying = true;
        this.showResult = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
    }
  }
 
};
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
