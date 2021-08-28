<template>
  <p>Bomb defuse time - {{ score }} ms</p>
  <p class="rank"> {{ rank }} </p>
</template>

<script>
export default {
  props: ['score'],
  data() {
    return {
      rank: null
    }
  },
  mounted() {
    if (this.score < 250) {
      this.rank = 'Great'
    } else if (this.score < 500) {
      this.rank = 'Nice'
    } else {
      this.rank = 'Almost!'
    }
  }
}
</script>

<style scoped>
  .rank {
    font-size: 1.4em;
    color: #0FAF87;
    font-weight: bold;
  }
</style>