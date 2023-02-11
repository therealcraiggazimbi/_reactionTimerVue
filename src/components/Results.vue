<template>
  <p>Reaction Time :{{ score }} ms</p>
  <p class="rank">{{ _rank }}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      _rank: null,
    };
  },

  mounted() {
    if (this.score < 250) {
      this._rank = "Ninja Fingers";
    } else if (this._score < 400) {
      this._rank = "Rapid Reflexes";
    } else {
      this._rank = "Snail pace...";
    }
  },
};
</script>

<style>
.rank {
  color: #0faf87;
  font-size: 2rem;
  font-weight: bold;
}
</style>
