<template>
  <div class="app">
    <br />
    <Header
      :headerNameColor="colorDisplay"
      :headerBackgroundColor="headerColor"
    />
    <Navbar
      :rb="restartButton"
      @eventRestart="restart"
      :ms="messageDisplay"
      :mode="getMode()"
      @changeMode="changeMode($event)"
    />
    <Keyboard :squareColors="colors" @eventEvalChoice="evalChoice($event)" />
  </div>
</template>

<script>
import Header from "./componentes/Header.vue";
import Navbar from "./componentes/Navbar.vue";
import Keyboard from "./componentes/Keyboard.vue";

export default {
  name: "App",
  components: {
    Header,
    Navbar,
    Keyboard,
  },
  data() {
    return {
      colorCount: 6,
      isHard: true,
      colors: [],
      pickedColor: 0,
      colorDisplay: "",
      headerColor: "",
      restartButton: "",
      messageDisplay: "",
    };
  },
  methods: {
    getMode() {
      return this.isHard;
    },

    changeMode(isHard) {
      this.isHard = isHard;
      this.colorCount = isHard ? 6 : 3;
      this.restart();
    },
    evalChoice(choice) {
      let colorChosen = this.colors[choice];
      if (colorChosen === this.pickedColor) {
        this.messageDisplay = "You Picked Right!";
        this.setAllColorsTo(this.pickedColor);
        this.restartButton = "Play Again!";
        this.headerColor = this.pickedColor;
      } else {
        this.colors.splice(choice, 1, "#232323");
        this.messageDisplay = "Try Again!";
        //this.colorDisplay = "#000000";
      }
    },
    setAllColorsTo(color) {
      let newColors = [];
      for (let i = 0; i < this.colorCount; i++) {
        newColors.push(color);
      }
      this.colors = newColors;
    },
    PickColor() {
      let quantity;
      if (this.isHard) {
        quantity = 6;
      } else {
        quantity = 3;
      }
      return Math.floor(Math.random() * quantity);
    },
    createNewColors(numbers) {
      let arr = [];
      for (let i = 0; i < numbers; i++) {
        arr.push(this.createRandomStringColor());
      }
      return arr;
    },
    createRandomStringColor() {
      let newColor =
        "rgb(" +
        this.randomInt() +
        ", " +
        this.randomInt() +
        ", " +
        this.randomInt() +
        ")";
      return newColor;
    },
    randomInt() {
      return Math.floor(Math.random() * 256);
    },
    restart() {
      this.colors = this.createNewColors(this.colorCount);
      this.pickedColor = this.colors[this.PickColor()];
      this.colorDisplay = this.pickedColor;
      this.textContent = "Pick New Colors!";
      this.headerColor = "steelblue";
      this.messageDisplay = "";
      this.restartButton = "New Colors!";
    },
  },

  mounted() {
    this.restart();
  },
};
</script>

<style>
.app {
  background: #232323;
  margin: 0;
  font-family: "Montserrat", "Avenir";
}
</style>
