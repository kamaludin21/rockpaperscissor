<template>
  <div
    class="
      flex
      justify-between
      items-center
      border-2 border-gray-400
      bg-gray-400
      rounded-t
      px-2
      pt-1
    "
  >
    <div class="flex-1">
      <p class="text-xs font-black">Computer</p>
      <p v-if="computerScore == 0">💤</p>
      <div class="flex" v-if="computerScore > 0">
        <div class="tracking-tight" :key="score" v-for="score in computerScore">
          <p>⭐</p>
        </div>
      </div>
    </div>
    <div class="flex-shrink-0">
      <p class="text-xl">✖</p>
    </div>
    <div class="flex-1 text-right">
      <p class="text-xs font-black">Human</p>
      <p v-if="humanScore == 0">💤</p>
      <div class="flex justify-end" v-if="humanScore > 0">
        <div :key="score" v-for="score in humanScore">
          <p>⭐</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Scoreboard",
  props: {
    computerScore: Number,
    humanScore: Number,
  },
};
</script>