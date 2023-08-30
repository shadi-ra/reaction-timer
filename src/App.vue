<template>
<h1>shadi reaction timer</h1>
<button @click="start" :disabled="isPlaying">play</button>
<Block v-if="isPlaying" :delay="delay" @end="endGame"/>
<p v-if="showResult">reactionTime: {{score}} ms</p>
</template>

<script>
import Block from './components/BlockComponent.vue'
import Result from './components/ResultComponent.vue'
export default {
  name: 'App',
  components:{
    Block
  },
data(){
  return{
    isPlaying:false,
    delay:null,
   score:null,
   showResult : false
  }
},
methods:{
  start(){
    this.delay = 2000 + Math.random()*5000
    this.isPlaying = true
this.showResult = false
  },
  endGame(input){
   this.score = input
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
  color: #444;
  margin-top: 60px;
}
</style>
