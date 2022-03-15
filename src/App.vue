<template>
  <h1>Reaction Timer</h1>
  <p>Test your reaction time by clicking on the pink element, that appears after a delay in the middle of the screen...</p>
  <button @click="start" :disabled="isPlaying">start timer</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data(){
    return{
      delay: null,
      isPlaying: false,
      score: null,
      showResults: false
    }
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    }
  }
}
</script>

<style>
#app {
  color: #2c3e50;
}
</style>
