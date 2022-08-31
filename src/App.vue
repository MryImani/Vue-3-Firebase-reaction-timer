<template>
  <h1>Reaction Timer</h1>
  <button class="startButton" @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" @showResult="stop" :delay="delay" />
  <Result v-if="!isPlaying" :score="score"/>
</template>


<script>
import Block from "./components/BlockComponent.vue";
import Result from "./components/Resultcomponent.vue";

export default {
  name: "App",
  components: {
    Result,
    Block,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      showResult: false,
      score:null
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
    },
    stop(reactionTime) {
      this.isPlaying = false;
      this.showResult = true;
      this.score = reactionTime ;
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
.startButton {
  background-color: #0faf87;
  padding: 10px;
  border-radius: 5px;
  color: #fff;
  border: none;
  cursor: pointer;
}
button[disabled]{
  opacity: 0.2;
  cursor:not-allowed;
}
</style>
