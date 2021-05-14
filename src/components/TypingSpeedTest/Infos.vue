<template>
  <div class="row align-items-start text-white">
    <div class="col bg-success">
      <p class="h1" style="font-size: 14pt">Correct words</p>
      <p style="font-size: 12pt">{{ hits }}</p>
    </div>
    <div class="col bg-danger">
      <p class="h1" style="font-size: 14pt">Wrong words</p>
      <p style="font-size: 12pt">{{ errors }}</p>
    </div>
    <div class="col bg-info">
      <p class="h1" style="font-size: 14pt">Time</p>
      <app-timer :end="end"></app-timer>
    </div>
  </div>
</template>

<script>
import AppTimer from "./Infos/Timer.vue";

export default {
  props: ["errors", "hits", "end"],
  components: {
    AppTimer,
  },
};
</script>

<style>
.col {
  height: 55px;
}
</style>