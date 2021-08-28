<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    Click
  </div>
</template>

<script>
export default {
  props: ['delay'],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0
    }
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer() {
      clearInterval(this.timer)
      this.$emit('end', this.reactionTime)
    }
  },
  mounted() {
    console.log('component mounted')
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },
  updated() {
    console.log('component updated')
  },
  unmounted() {
    console.log('component unmounted')
  }
}
</script>

<style scoped>
  .block {
    width: 25em;
    border-radius: 1.25em;
    background: #0FAF87;
    color: white;
    text-align: center;
    padding: 6.25em 0;
    margin: 2.5em auto;
  }
</style>