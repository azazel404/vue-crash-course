<template>
  <p>Reaction time - {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    //props
  props: ['score'],
  //state
  data() {
    return {
      rank : null
    }
  },
  //life cycle hooks
  mounted() {
    if (this.score < 250) {
      this.rank = 'Ninja Fingers'
    } else if (this.score < 400) {
      this.rank = 'Rapid Reflexes'
    } else {
      this.rank = '...Snail Pace'
    }
  }
}
</script>

<style>
  .rank {
    font-size: 1.4em;
    color: black;
    font-weight: bold;
  }
</style>