<template>
  <div
    class="border-2 border-gray-400 py-5 space-y-2"
    v-if="roundWinner != null"
  >
    <img class="w-1/3 mx-auto" :src="imageResource" alt="Winner and loser" />
    <div class="text-center">
      <p class="text-3xl font-bold">{{ computerScore }} : {{ humanScore }}</p>
      <p class="text-xl font-bold">
        YOU {{ roundWinner === "human" ? "WIN" : "LOSE" }}
      </p>
      <hr class="my-2" />
      <p class="font-light">Click/select round to play again</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "RoundResult",
  props: {
    roundWinner: String,
    computerScore: Number,
    humanScore: Number
  },
  computed: {
    imageResource: function () {
      return this.roundWinner == "human"
        ? "https://ik.imagekit.io/n0t5masg5jg/rockpaperscissor/win__1__kmEghbVs6w.png"
        : "https://ik.imagekit.io/n0t5masg5jg/rockpaperscissor/lose_6oXrTA7dLH5H.png";
    },
  },
};
</script>