<template>
  <div>
    <p>
      <span id="time" v-html="time" style="font-size: 12pt"></span>
    </p>
    <div v-if="end === true">
      <div v-on="pause()"></div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["end"],
  data() {
    return {
      state: "started",
      startTime: Date.now(),
      currentTime: Date.now(),
      interval: null,
    };
  },
  mounted() {
    this.interval = setInterval(this.updateCurrentTime, 1000);
  },
  destroyed() {
    clearInterval(this.interval);
  },
  computed: {
    time() {
      return this.minutes + ":" + this.seconds;
    },
    milliseconds() {
      return this.currentTime - this.$data.startTime;
    },
    minutes() {
      var lapsed = this.milliseconds;
      var min = Math.floor((lapsed / 1000 / 60) % 60);
      return min >= 10 ? min : "0" + min;
    },
    seconds() {
      var lapsed = this.milliseconds;
      var sec = Math.ceil((lapsed / 1000) % 60);
      return sec >= 10 ? sec : "0" + sec;
    },
  },
  methods: {
    reset() {
      this.$data.state = "started";
      this.$data.startTime = Date.now();
      this.$data.currentTime = Date.now();
    },
    pause() {
      this.$data.state = "paused";
    },
    resume() {
      this.$data.state = "started";
    },
    updateCurrentTime() {
      if (this.$data.state == "started") {
        this.currentTime = Date.now();
      }
    },
  },
};
</script>

<style>
</style>