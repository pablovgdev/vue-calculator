<template>
	<a href="#">
		<div class="button" @click="addValue">{{ value }}</div>
	</a>
</template>

<script>
import { EventBus } from "../main.js";

export default {
  props: ["value"],
  methods: {
    addValue() {
      EventBus.$emit("addValue", this.value);
    }
  }
};
</script>

<style scoped>
.button {
  width: 60px;
  height: 60px;
  margin: 5px;
  background-color: darkgray;
  border: none;
  border-radius: 10px;
  display: inline-block;
  text-align: center;
  color: white;
  line-height: 60px;
  font-size: 22px;
  border: 1px solid rgba(0, 0, 0, 0.4);
}
</style>