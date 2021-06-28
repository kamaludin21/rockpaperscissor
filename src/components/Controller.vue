<template>
  <div class="border-t border-gray-200 bg-gray-200">
    <div class="flex items-center space-x-2 text-center px-2 h-28" v-if="!afterClick">
      <div class="flex-1" v-for="hand in hands" :key="hand">
        <div class="selection-button" @click="clickButton(hand)">
        <p class="selection-text uppercase">{{ hand }}</p>
      </div>
      </div>
    </div>
    <div class="text-center flex justify-center h-28" v-if="afterClick">
      <Loading v-if="loading" />
      <div class="w-3/4 md:w-2/3 flex justify-center items-center space-x-2" v-if="!loading">
        <img
          class="w-1/3 md:w-1/4"
          :src=imageResource
          alt=""
        />
        <div class="text-center">
          <p class="text-lg font-medium">YOU {{ (turnWinner == 'human') ? 'WIN' : 'LOSE' }}</p>
          <p class="text-sm font-light leading-none">
            {{ (turnWinner == 'human') ? 'Congratulations' : 'Try again' }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Loading from './Loading.vue'

export default {
  name: "Controller",
  components: {
    Loading
  },
  props: {
    hands: Object,
    afterClick: Boolean,
    turnWinner: String,
    loading: Boolean
  },
  methods: {
    clickButton: function (value) {
      this.$emit("get-human-choice", value);
    },
  },
  computed: {
    imageResource: function () {
      return this.turnWinner == 'human' ? 'https://ik.imagekit.io/n0t5masg5jg/rockpaperscissor/win__1__kmEghbVs6w.png' : 'https://ik.imagekit.io/n0t5masg5jg/rockpaperscissor/lose_6oXrTA7dLH5H.png'
    }
  },
  emits: ["get-human-choice"]
};
</script>

<style scoped lang="postcss">
.selection-button {
  @apply duration-500 rounded py-6 md:p-6 px-2 border-2 border-gray-400 bg-gray-400 hover:bg-gray-600 cursor-pointer;
}

.selection-text {
  @apply text-gray-200 hover:text-gray-50 font-bold text-xl md:text-2xl
}
</style>