<template>
  <h1>Ka-boom</h1>
  <button @click="start" :disabled="isPlaying" >Defuse!</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Result v-if="showResult" :score="score"></Result>
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },
  components: {
    Block,
    Result
  },
  methods: {
    start() {
      this.delay = 500 + Math.random()*5000
      this.isPlaying = true
      this.showResult = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  background: #0FAF87;
  color: white;
  border: none;
  padding: 0.5em 1em;
  border-radius: 0.25em;
  font-size: 1em;
  letter-spacing: 0.0625em;
  cursor: pointer;
  margin: 0.625em;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
