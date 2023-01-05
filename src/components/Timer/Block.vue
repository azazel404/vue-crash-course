<template>
  <div class="block" v-show="showBlock" @click="stopTimer">click me fast</div>
</template>

<script>
export default {
//props
  props: ["delay"],
  //state
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
//   lifecycle hooks
//mouting running the timer
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods : {
     startTimer() {
      // start the timer, tick every 10ms
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer() {
      // stop the timer
      clearInterval(this.timer)
      //callback func with param
      this.$emit('endThisGame', this.reactionTime)
    }
  }
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
