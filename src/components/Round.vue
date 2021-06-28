<template>
  <Title title="Choose round" />
  <div class="flex style-wrapper">
    <div class="flex-1" :key="round" v-for="round in rounds">
      <div
        class="style-button"
        :class="[activeRound == round ? 'active' : 'inactive']"
        @click="clickRound(round)"
      >
        <p class="style-text text-center">{{ round }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import Title from "./Title";

export default {
  name: "Round",
  components: {
    Title,
  },
  props: {
    activeRound: String,
    rounds: Object,
  },
  methods: {
    clickRound: function(round) {
      this.$emit("change-round", round);
    }
  },
  emits: ["change-round"]
};
</script>