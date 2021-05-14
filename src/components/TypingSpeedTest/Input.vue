<template>
  <div class="input-group" style="padding: 10px;">
    <textarea
      v-model="text"
      v-on="event()"
      class="form-control"
      aria-label="With textarea"
    ></textarea>
  </div>
</template>

<script>
export default {
  data() {
    return {
      text: "",
    };
  },
  methods: {
    event() {
      this.$emit("text", this.text);
    },
  },
};
</script>

<style>
</style>