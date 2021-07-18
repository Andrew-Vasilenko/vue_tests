<template>
	<p>
		<ul>
			<TodoItem
				v-for = "todoItem in todoList"
				v-bind:todoItem = "todoItem"
				v-bind:key = "todoItem.id"
				v-on:todoItemRemove = "todoItemRemove"
			/>
		</ul>
	</p>
</template>

<script>
	// импорт компонентов
	import TodoItem from '@/components/TodoItem'

	export default {
		props: ['todoList'],
		// регистрация компонентов
		components: {
			TodoItem:TodoItem
		},
		methods: {
			todoItemRemove(todoItemId) {
				this.$emit('todoItemRemove', todoItemId)
				console.log(todoItemId + " AAAAAAA")
			}
		}
	}
</script>

<style scoped>
	ul {
		list-style: none;
		margin: 0;
		padding: 0;
	}
</style>