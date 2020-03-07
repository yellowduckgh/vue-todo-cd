<template>
	<div>
		<!-- TodoHeader todo-header 두개 다 똑같이 써도 된다 -->
		<TodoHeader></TodoHeader>
		<todo-input v-on:add-todo="addTodoItem"></todo-input>
		<todo-list
			v-bind:list="todoItems"
			v-on:remove-item="removeTodoItem"
		></todo-list>
		<todo-footer v-on:clear="clearAllItems"></todo-footer>
	</div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoFooter from './components/TodoFooter.vue';

//vim

export default {
	components: {
		// 'todo-header': TodoHeader,
		// 'todo-input': TodoInput,
		// 'todo-list': TodoList,
		// 'todo-footer': TodoFooter,
		TodoHeader,
		TodoInput,
		TodoList,
		TodoFooter,
	},
	//vda + tab
	data() {
		return {
			todoItems: [],
		};
	},
	methods: {
		fetchItems: function() {
			for (var i = 0; i < localStorage.length; i++) {
				var item = localStorage.key(i);
				this.todoItems.push(item);
			}
		},
		addTodoItem: function(value) {
			this.todoItems.push(value);
			localStorage.setItem(value, value);
		},
		removeTodoItem: function(item, index) {
			this.todoItems.splice(index, 1);
			localStorage.removeItem(item);
		},
		clearAllItems: function() {
			this.todoItems = [];
			localStorage.clear();
		},
	},
	created: function() {
		//console.log('created');
		this.fetchItems();
	},
};
</script>

<style></style>
