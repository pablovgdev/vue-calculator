<template>
	<div id="body">
		<screen :value="output"></screen>
		<button-wrap></button-wrap>
	</div>
</template>

<script>
import Screen from "./Screen.vue";
import ButtonWrap from "./ButtonWrap.vue";
import { EventBus } from "../main.js";

export default {
  data() {
    return {
      output: "0",
      lastIsChar: false
    };
  },
  components: {
    Screen,
    ButtonWrap
  },
  mounted() {
    EventBus.$on("addValue", value => {
      if (this.output === "0" && typeof value == "number") {
        this.output = value.toString();
      } else if (value == "," && this.output != "0") {
        this.output = parseFloat(this.output)
          .toFixed(2)
          .toString();
      } else {
        if (value == "=" && this.output != "0" && !this.lastIsChar) {
          let arr = this.output.split(/([/x+-]+)/g);
          let calculation = 0;

          while (arr.length != 1) {
            if (arr.indexOf("/") != -1) {
              let pos = arr.indexOf("/");

              calculation = parseFloat(arr[pos - 1]) / parseFloat(arr[pos + 1]);

              arr.splice(pos - 1, 1);
              arr.splice(pos - 1, 1);
              arr.splice(pos - 1, 1, calculation.toFixed(2).toString());
              console.table(arr);
              console.log(calculation);
              continue;
            }

            if (arr.indexOf("x") != -1) {
              let pos = arr.indexOf("x");

              calculation = parseFloat(arr[pos - 1]) * parseFloat(arr[pos + 1]);

              arr.splice(pos - 1, 1);
              arr.splice(pos - 1, 1);
              arr.splice(pos - 1, 1, calculation.toFixed(2).toString());
              console.table(arr);
              console.log(calculation);
              continue;
            }

            if (arr.indexOf("-") != -1) {
              let pos = arr.indexOf("-");

              calculation = parseFloat(arr[pos - 1]) - parseFloat(arr[pos + 1]);

              arr.splice(pos - 1, 1);
              arr.splice(pos - 1, 1);
              arr.splice(pos - 1, 1, calculation.toFixed(2).toString());
              console.table(arr);
              console.log(calculation);
              continue;
            }

            if (arr.indexOf("+") != -1) {
              let pos = arr.indexOf("+");

              calculation = parseFloat(arr[pos - 1]) + parseFloat(arr[pos + 1]);

              arr.splice(pos - 1, 1);
              arr.splice(pos - 1, 1);
              arr.splice(pos - 1, 1, calculation.toFixed(2).toString());
              console.table(arr);
              console.log(calculation);
              continue;
            }
          }

          this.output = calculation.toString();
        } else {
          if (typeof value === "number") {
            this.output += value.toString();
            this.lastIsChar = false;
          } else {
            !this.lastIsChar && this.output != "0"
              ? (this.output += value)
              : "";
            this.lastIsChar = true;
          }
        }
      }
    });
  }
};
</script>

<style scoped>
#body {
  width: 350px;
  height: 470px;
  background-color: orange;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
  border-radius: 10px;
  border: 1px solid rgba(0, 0, 0, 0.4);
}
</style>