<template>
  <div>
  <h1>REACTION TIMER GAME</h1>
  <button @click="start" :disabled="isplaying">Play</button>
  </div>
  <Block v-if="isplaying" :delay="delay" @end="endGame"/>
  <Result v-if="showresult" :score="score"/>
  <!-- <p v-if="showresult">Reaction Time: {{ score }} ms </p> -->

</template>

<script>  
import Block from  './components/block.vue'
import Result from  './components/result.vue'

export default{
  name: 'App',
  components: { Block , Result },
  data() { 
    return {
      isplaying: false,
      delay: null,
      score: null,
      showresult: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isplaying = true
      // console.log(this.delay);
      this.showresult = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isplaying = false
      this.showresult = true
    }
  }
}
</script>

<style>

</style>
