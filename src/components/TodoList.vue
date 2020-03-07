<template>
	<ul>
		<li v-for="(item, index) in list" v-bind:key="index">
			<span>{{ item }}</span>
			<button v-on:click="removeItem(item, index)">remove</button>
		</li>
	</ul>
</template>

<script>
import { bus } from '../utils/bus';

export default {
	//props:['list'],
	props: {
		list: Array,
	},

	// data() {
	// 	return {
	// 		todoItems: [],
	// 	};
	// },
	methods: {
		// fetchItems: function() {
		// 	for (var i = 0; i < localStorage.length; i++) {
		// 		var item = localStorage.key(i);
		// 		this.todoItems.push(item);
		// 	}
		// },
		removeItem: function(item, index) {
			//console.log(event);
			//console.log('clicked', item, index);

			this.$emit('remove-item', item, index);
			// this.todoItems.splice(index, 1);
			// localStorage.removeItem(item);
		},
		removeItems: function() {
			this.todoItems = [];
		},
	},
	// created: function() {
	// 	//console.log('created');
	// 	this.fetchItems();
	// },
	beforeMount: function() {
		bus.$on('remove-all', this.removeItems);

		//console.log('before mount');
		//JSON.part()
		//JSON.stringify()
	},
	beforeDestroy: function() {
		bus.$off('remove-all');
	},
};
</script>

<style></style>
