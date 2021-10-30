<template>
  <p>Reaction Time : {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  name: "Results",
  props: {
    score: {
      type: Number,
      required: true,
    },
  },

  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    console.log("this.score", this.score);
    if (this.score < 1000) {
      this.rank = "Ninja Fingers";
    } else if (this.score < 3000) {
      this.rank = "Rapid Reflexes";
    } else if (this.score > 3000) {
      this.rank = "Snail pace";
    }
  },
};
</script>

<style scoped>
.rank {
  font-size: 1.4rem;
  color: #0faf87;
  font-weight: bold;
}
</style>
