<template>
	<div class="button-row">
		<c-button v-for="value in values" :key="value" :value="value"></c-button>
	</div>
</template>

<script>
import Button from "./Button.vue";

export default {
  props: ["values"],
  components: {
    cButton: Button
  }
};
</script>

<style scoped>
.button-row {
  width: 300px;
  height: 70px;
  margin: 0 auto;
}
</style>