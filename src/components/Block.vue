<template>
  <div class="block" v-if="showBlock" @click="stopTimer">click me</div>
</template>

<script>
export default {
  name: "Block",
  props: {
    delay: {
      type: Number,
      required: true,
    },
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      console.log("this.reactionTime", this.reactionTime);
      this.$emit("end", this.reactionTime);
    },
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  updated() {
    console.log("updated");
  },
  beforeUpdate() {
    console.log("before updated");
  },
  unmounted() {
    console.log("unmounted");
  },
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
};
</script>

<style scoped>
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
