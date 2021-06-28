<template>
  <div class="flex justify-center items-center">
      <div class="flex-1">
        <img
          class="w-28 md:w-36 mx-auto"
          :src=baseUrlImage+computerHand
          alt="computer choice"
          loading="eager"
        />
      </div>
      <div class="flex-shrink-0">
        <img
          class="w-10 md:w-14 mx-auto"
          src="https://ik.imagekit.io/n0t5masg5jg/rockpaperscissor/vs__2__CeafPJpVAP1_.png"
          alt="vs"
          loading="eager"
        />
      </div>
      <div class="flex-1">
        <img
          class="w-28 md:w-36 mx-auto"
          :src=baseUrlImage+humanHand
          alt="human choice"
          loading="eager"
        />
      </div>
    </div>
</template>

<script>
export default {
  name: "Arena",
  props: {
    baseUrlImage: String,
    computerHand: String,
    humanHand: String
  }
};
</script>