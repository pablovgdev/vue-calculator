<template>
	<div id="screen">
		<div id="calculation">{{ value }}</div>
	</div>
</template>

<script>
export default {
  props: {
    value: String
  }
};
</script>

<style scoped>
#screen {
  width: 300px;
  height: 40px;
  background-color: lightgray;
  border-radius: inherit;
  margin: 25px auto;
  padding-top: 40px;
  border: 1px solid rgba(0, 0, 0, 0.4);
}

#calculation {
  widows: 280px;
  height: 40px;
  color: black;
  text-align: right;
  padding-right: 20px;
  font-size: 28px;
  overflow: hidden;
}
</style>