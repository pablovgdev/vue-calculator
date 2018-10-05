<template>
    <div id="App">
        <calculator></calculator>
    </div>
</template>

<script>
import Calculator from "./components/Calculator.vue";

export default {
  components: {
    Calculator
  }
};
</script>

<style>
#App {
  text-align: center;
  font-family: sans-serif;
}

html,
body {
  background-color: lightblue;
}
</style>
