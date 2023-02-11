<template>
  <div class="block" v-if="_showBlock" @click="_stopTimer">Click Me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      _showBlock: false,
      _timer: null,
      _reactionTime: 0,
    };
  },
  mounted() {
    console.log("component mounted");
    setTimeout(() => {
      this._showBlock = true;
      this._startTimer();
    }, this.delay);
  },

  methods: {
    _startTimer() {
      this._timer = setInterval(() => {
        this._reactionTime += 10;
      }, 10);
    },

    _stopTimer() {
      clearInterval(this._timer);
      this.$emit("end", this._reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
