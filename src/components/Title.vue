<template>
  <div
    class="
      border-b border-black border-opacity-0
      hover:border-opacity-100
      w-max
      cursor-pointer
    "
  >
    <p class="font-light text-sm">{{ title }}</p>
  </div>
</template>

<script>
export default {
  name: "Title",
  props: {
    title: String,
  },
};
</script>