<template>
  <div class="border-t border-gray-200">
    <div class="flex items-center space-x-4 text-center px-2 h-24 md:h-36" v-if="show">
      <div class="selection-button">
        <p>ROCK</p>
      </div>
      <div class="selection-button">
        <p>ROCK</p>
      </div>
      <div class="selection-button">
        <p>ROCK</p>
      </div>
    </div>
    <div class="text-center flex justify-center h-24 md:h-32" v-if="!show">
      <div class="w-3/4 md:w-2/3 flex justify-center items-center space-x-2">
        <img
          class="w-1/3"
          src="https://ik.imagekit.io/n0t5masg5jg/rockpaperscissor/lose_6oXrTA7dLH5H.png"
          alt=""
        />
        <div class="text-left">
          <p class="text-lg font-medium">YOU LOSE</p>
          <p class="text-sm font-light leading-none">
            Choose the round above if you want to play again
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Controller",
  data() {
    return {
      show: false,
    //   show: false,
    };
  },
};
</script>

<style scoped lang="postcss">
.selection-button {
  @apply flex-1 duration-500 rounded p-6 border-2 border-gray-400 hover:bg-gray-400 cursor-pointer;
}
</style>