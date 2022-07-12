<template>
   <h1>Reaction Time Game</h1>
   <button @click="start" class="btn">Start</button>
   <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
   <Results v-if="showResults" :score="score"/>
   <Display v-if="showDisplay" :isPlaying="isPlaying" @disq="disqualified" @closeOverlay="closeOverlay" :error="error"/>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
import Display from './components/Display.vue'
export default {
  name: 'App',
  components: { Block, Results, Display },
  data() {
    return {
      delay: null,
      isPlaying: false,
      score: 0,
      showResults: false,
      showDisplay: false,
      error: null
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
      this.showDisplay = true
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
      this.showDisplay = false
    },
    disqualified() {
      this.error = 'You clicked the wrong button, so you are disqualified'
      this.isPlaying = false
    },
    closeOverlay() {
      this.error = false
      this.showDisplay = false
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
.btn {
  padding: 15px 25px;
  background-color: rgb(9, 39, 39);
  border: none;
  border-radius: 5px;
  color: #fff;
  cursor: pointer;
}
</style>
