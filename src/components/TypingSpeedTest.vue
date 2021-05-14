<template>
  <div id="Typing">
     <div v-if="end == true">
        <p>
          end!
        </p>
      </div>
    <div
      style="display: inline-block"
      v-for="(value, index) in wordsList"
      :key="value.word"
    >
      <p
        v-if="index === 0"
        class="lead"
        style="
          padding: 5px;
          background-color: #abb6c0;
          border-radius: 5px;
          font-size: 18pt;
        "
      >
        {{ value }}
      </p>
      <p v-else class="lead" style="padding: 5px; font-size: 14pt">
        {{ value }}
      </p>
    </div>
    <Input @text="text = $event" v-on="stringCompare()"/>
    <p class="h6">{{ text }}</p>
    <Infos :errors="errors" :hits="hits" :end="end"/>
  </div>
</template>

<script>
import Input from "./TypingSpeedTest/Input.vue";
import Infos from "./TypingSpeedTest/Infos.vue";

export default {
  name: "Typing",
  data() {
    return {
      text: "",
      wordsList: [
        "first",
        "second",
        "third",
        "fourth",
        "fifth",
        "sixth",
        "seventh",
        "eighth",
        "ninth",
        "tenth",
      ],
      cont: 0,
      errors: 0,
      hits: 0,
      end: false,
    };
  },
  components: {
    Input,
    Infos,
  },
  methods: {
    stringCompare() {
      if (this.wordsList.length === 0) {
        this.end = true;
        return;
      }
      var text = this.text.split(" ");
      if (text[this.cont] === this.wordsList[0]) {
        this.cont++;
        this.wordsList.shift();
        this.hits++;
      } else if (text.length - 1 > this.cont) {
        this.cont++;
        this.wordsList.shift();
        this.errors++;
      }
    },
  },
};
</script>
