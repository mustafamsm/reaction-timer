<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying" class="btn">play</button>

  <Block v-if="isPlaying"  :delay="delay" @end="stope" />
  <Results v-if="score !==null" :score="score"/>
</template>

<script>
import Block from './components/Block.vue';
import Results from './components/Results.vue';
export default {
  
  name: 'App',
  components: { Block ,Results},
  data() {
    return {
      isPlaying: false,
      delay: null,
      score:null,
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 3000;
      this.isPlaying = true;
   
    },
    stope(reactionTime) {
      this.isPlaying = false;
      this.score=reactionTime *10;
  }
}
};
</script>

<style >
#app{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  text-align: center;
  margin-top: 50px;
}
.btn{
  padding: 10px 20px;
  font-size: 16px;
  border-radius: 5px;
  background-color: #42b983;
  color: white;
  border: none;
  cursor: pointer;
}
.btn:disabled {
  background-color: #a5d6a7;
  cursor: not-allowed;
}
</style>
