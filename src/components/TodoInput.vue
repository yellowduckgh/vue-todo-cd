<template>
	<div>
		<input type="text" v-model="inputText" />
		<button v-on:click="addItem">add</button>
	</div>
</template>

<script>
export default {
	data: function() {
		return {
			inputText: '',
		};
	},
	methods: {
		addItem: function() {
			var value = this.inputText;
			//localStorage.setItem(value, value);
			this.$emit('add-todo', value);
			this.clearInput();
		},
		clearInput: function() {
			this.inputText = '';
		},
	},
};
</script>

<style></style>
