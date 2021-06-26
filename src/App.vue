<template>
  <div class="app-wrapper">
    <div class="title-wrapper">
      <h1 class="title-style">ROCK PAPER SCISSOR</h1>
    </div>
    <div class="setting-wrapper">
      <Style :styles="styles" @change-image-style="changeImageStyle($event)" />
      <Round :rounds="rounds"/>
    </div>
    <Scoreboard />
    <div class="border-2 border-gray-400 pt-4 space-y-4">
      <Arena />
      <Controller />
    </div>
  </div>
</template>

<script>
import Style from "./components/Style";
import Round from "./components/Round";
import Arena from "./components/Arena";
import Scoreboard from './components/Scoreboard.vue';
import Controller from './components/Controller.vue';

export default {
  name: "App",
  components: {
    Style,
    Round,
    Arena,
    Scoreboard,
    Controller
  },
  data() {
    return {
      styles: [
        { name: "FLAT", url: "flat" },
        { name: "LINEAL", url: "lineal" },
        { name: "LINEAL COLOR", url: "linealcolor" },
        { name: "BLUE", url: "blue" },
        { name: "FILL", url: "fill" },
      ],
      rounds: ["1", "3", "5", "7"],
    };
  },
  methods: {
    changeImageStyle: function (value) {
      // this.baseUrl = value;
      console.log(value);
    },
  },
};
</script>

<style lang="postcss">
.app-wrapper {
  @apply w-full md:w-1/3 mx-auto p-2;
}

.title-wrapper {
  @apply w-max border-b-4 border-gray-600 hover:border-gray-700 text-gray-600 hover:text-gray-700 cursor-pointer mb-2;
}

.title-style {
  @apply font-black text-2xl select-none;
}

.setting-wrapper {
  @apply border-2 border-gray-400 px-2 pt-1 rounded mb-2;
}
</style>
