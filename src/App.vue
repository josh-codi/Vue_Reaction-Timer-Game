<template>
  <h1>welcome</h1>

  <button @click="start" :disable="isPlaying">Play</button>
  <Blog v-if="isPlaying" :delay="delay" @end="endGame" />
  
  <Result v-if="score" :score="score" @playAgain="start" @endGame="terminateGame"/>
  
</template>

<script>
import Blog from './components/Blog.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: { Blog, Result },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.score = null
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
    },
    terminateGame(){
      this.isPlaying = false
      this.delay = null
      this.score = null
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
  color: #444;
  margin-top: 60px;
}
</style>
