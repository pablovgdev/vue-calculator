<template>
	<div id="button-wrap">
		<button-row v-for="(row, i) in rows" :key="i" :values="row"></button-row>
	</div>
</template>

<script>
import ButtonRow from "./ButtonRow.vue";

export default {
  data() {
    return {
      rows: [[7, 8, 9, "/"], [4, 5, 6, "x"], [1, 2, 3, "-"], [",", 0, "=", "+"]]
    };
  },
  components: {
    ButtonRow
  }
};
</script>

<style scoped>
#button-wrap {
  width: 300px;
  height: 280px;
  margin: 40px auto;
}
</style>