<template>
  <h1>Reaction test</h1>
  <button :disabled="isPlaying" @click="start">Start new game</button>
  <Block :delay="delay" v-if="isPlaying" @end="endGame" />
  <Results :score="score" v-if="showResults" />
</template>

<script>
import Block from "@/components/Block.vue";
import Results from "@/components/Results.vue";
import Alert from "@/components/Alert.vue";

export default {
  name: "App",
  components: {
    Block,
    Results,
    Alert,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
      preFire: false,
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      this.showResults = false;
      this.preFire = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
</script>

<style>
#app {
  font-family: "Montserrat", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: teal;
  margin-top: 60px;
}

.alert-area {
  top: 0;
  position: fixed;
  width: 100%;
  height: 100%;
  margin-top: 200px;
}
</style>
