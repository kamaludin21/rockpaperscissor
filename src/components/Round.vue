<template>
  <Title title="Choose round" />
  <div class="flex style-wrapper">
    <div class="flex-1" :key="round" v-for="round in rounds">
      <div
        class="style-button"
        :class="[activeRound == round ? 'active' : 'inactive']"
        @click="clickStyle(round)"
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
  data() {
    return {
      activeRound: 3,
    };
  },
  props: {
    rounds: Object,
  },
};
</script>