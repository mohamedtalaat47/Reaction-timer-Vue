<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Block,Results
  },
  data(){
    return{
      isPlaying:false,
      delay:null,
      score:null,
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
  font-family: 'Open Sans', sans-serif;  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button{
  background: #0faf87;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  color: white;
  margin: 10px;
  padding: 8px 16px;
  font-size: 18px;
}
button[disabled]{
opacity: 0.2;
cursor: not-allowed;
}
</style>
