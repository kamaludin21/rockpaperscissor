<template>
  <Title title="Choose style" />
  <div class="style-wrapper">
    <div :key="style" v-for="style in styles">
      <div
        class="style-button"
        :class="[activeStyle == style.url ? 'active' : 'inactive']"
        @click="clickStyle(style.url)"
      >
        <p class="style-text">{{ style.name }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import Title from "./Title";

export default {
  name: "Style",
  components: {
    Title,
  },
  props: {
    activeStyle: String,
    styles: Object,
  },
  methods: {
    clickStyle: function (style) {
      //[1.a] for send data onclick to parent
      this.$emit("change-image-style", style);
    },
  },
  emits: ["change-image-style"]
};
</script>

<style lang="postcss">
.style-wrapper {
  @apply flex flex-row space-x-2 text-white py-2 items-center w-full;
}
.style-button {
  @apply transition duration-500 ease-in-out bg-gray-400 hover:bg-gray-500 transform hover:-translate-y-0 hover:scale-110 py-2 px-2 rounded cursor-pointer;
}

.active {
  @apply bg-gray-600;
}

.inactive {
  @apply bg-gray-400;
}

.style-text {
  @apply text-xs font-medium select-none;
}
</style>