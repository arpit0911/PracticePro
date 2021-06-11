<template>
  <h1>Ninja Reaction Timer</h1>
  <button class="btn" @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showScore" :score="score"/>

</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: { Block , Results},
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showScore: false,

    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showScore=false
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.showScore= true
      this.isPlaying= false
    },
  },
};
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
.btn{
  text-align:  center;
  padding: 10px 20px ;
  background-color: rgb(69, 170, 170);
  border-radius: 4px;
  border : 1px solid rgb(14, 42, 51);
  cursor: pointer;
  font-size: 16px;
  letter-spacing: 1px;
  text-decoration: none;
  color: white;
  
}
.btn:hover{
  background-color: rgb(57, 143, 143) ;
}
.btn[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
