<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="_isPlaying">Play</button>
  <Block v-if="_isPlaying" :delay="_delay" @end="_endGame" />
  <Results v-if="_showResults" :score="_score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: {
    Block,
    Results,
  },
  data() {
    return {
      _isPlaying: false,
      _delay: null,
      _score: null,
      _showResults: false,
    };
  },
  methods: {
    start() {
      this._delay = 2000 + Math.random() * 5000;
      this._isPlaying = true;
      this._showResults = false;
    },

    _endGame(_reactionTime) {
      this._score = _reactionTime;
      this._isPlaying = false;
      this._showResults = true;
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
  color: #2c3e50;
  margin-top: 60px;
}

button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
