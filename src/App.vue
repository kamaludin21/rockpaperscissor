<template>
  <div class="app-wrapper">
    <div class="title-wrapper">
      <h1 class="title-style"><a href="https://kamaludin.tech/">ROCK PAPER SCISSOR</a></h1>
    </div>
    <div class="setting-wrapper">
      <Style
        :activeStyle="activeStyle"
        :styles="styles"
        @change-image-style="changeImageStyle($event)"
      />
      <Round
        :activeRound="activeRound"
        :rounds="rounds"
        @change-round="changeRound($event)"
      />
    </div>
    <Scoreboard :computerScore="computerScore" :humanScore="humanScore" />
    <div
      class="border-2 border-gray-400 bg-gray-100 pt-4 space-y-4"
      v-if="roundWinner == null"
    >
      <Arena
        :baseUrlImage="baseUrlImage"
        :computerHand="computerHand"
        :humanHand="humanHand"
      />
      <Controller
        :hands="hands"
        :turnWinner="turnWinner"
        :loading="loading"
        @get-human-choice="startGame($event)"
        :afterClick="afterClick"
      />
    </div>
    <RoundResult
      :roundWinner="roundWinner"
      :computerScore="computerScore"
      :humanScore="humanScore"
    />
  </div>
</template>

<script>
import Style from "./components/Style";
import Round from "./components/Round";
import Arena from "./components/Arena";
import Scoreboard from "./components/Scoreboard";
import Controller from "./components/Controller";
import RoundResult from "./components/RoundResult";

export default {
  name: "App",
  components: {
    Style,
    Round,
    Scoreboard,
    Arena,
    Controller,
    RoundResult,
  },
  data() {
    return {
      baseUrlImage: "https://ik.imagekit.io/n0t5masg5jg/rockpaperscissor/flat/",
      styles: [
        { name: "FLAT", url: "flat" },
        { name: "LINEAL", url: "lineal" },
        { name: "LINEAL COLOR", url: "linealcolor" },
        { name: "BLUE", url: "blue" },
        { name: "FILL", url: "fill" },
      ],
      rounds: ["1", "3", "5", "7"],
      hands: ["rock", "paper", "scissor"],
      activeStyle: "flat",
      activeRound: "3",
      computerHand: "rock.png",
      humanHand: "rock.png",
      turnWinner: null,
      roundWinner: null,
      humanScore: 0,
      computerScore: 0,
      afterClick: false,
      loading: false,
    };
  },
  methods: {
    changeImageStyle: function (value) {
      let url = "https://ik.imagekit.io/n0t5masg5jg/rockpaperscissor/";
      this.activeStyle = value;
      this.baseUrlImage = url + value + "/";
    },
    changeRound: function (value) {
      (this.turnWinner = null),
        (this.roundWinner = null),
        (this.humanScore = 0),
        (this.computerScore = 0),
        (this.afterClick = false);
      this.activeRound = value;
    },
    startGame: function (humanChoice) {
      this.shuffleComputerChoice();
      this.afterClick = true;
      this.loading = true;
      this.humanHand = humanChoice + ".png";

      let computerChoice =
        this.hands[Math.floor(Math.random() * this.hands.length)];
      let getWinner = this.chooseWinner(computerChoice, humanChoice);
      setTimeout(() => {
        this.computerHand = computerChoice + ".png";
        if (getWinner == "win") {
          this.turnWinner = "human";
          this.humanScore++;
          if (this.humanScore == this.activeRound) {
            setTimeout(() => {
              this.roundWinner = "human";
            }, 2000);
          } else {
            setTimeout(() => {
              this.afterClick = false;
            }, 1000);
          }
        } else if (getWinner == "lose") {
          this.turnWinner = "computer";
          this.computerScore++;
          if (this.computerScore == this.activeRound) {
            setTimeout(() => {
              this.roundWinner = "computer";
            }, 2000);
          } else {
            setTimeout(() => {
              this.afterClick = false;
            }, 1000);
          }
        } else {
          this.afterClick = false;
        }
        this.loading = false;
        clearInterval(this.shuffelInterval);
      }, 750);
    },
    chooseWinner: function (computer, human) {
      if (human === computer) return "draw";
      if (human === "rock") return computer === "scissor" ? "win" : "lose";
      if (human === "paper") return computer === "rock" ? "win" : "lose";
      if (human === "scissor") return computer === "paper" ? "win" : "lose";
    },
    shuffleComputerChoice: function () {
      let i = 0;
      this.shuffelInterval = setInterval(() => {
        this.computerHand = this.hands[i++] + ".png";
        if (i == this.hands.length) i = 0;
      }, 150);
    },
  },
};
</script>

<style lang="postcss">
.app-wrapper {
  @apply w-full md:w-1/3 mx-auto p-2;
}

.title-wrapper {
  @apply flex items-center space-x-2 w-max border-b-4 border-gray-600 hover:border-gray-700 text-gray-600 hover:text-gray-700 cursor-pointer mb-2;
}

.title-style {
  @apply font-black text-2xl select-none;
}

.setting-wrapper {
  @apply border-2 border-gray-400 bg-gray-100 px-2 pt-1 rounded mb-2;
}
</style>
