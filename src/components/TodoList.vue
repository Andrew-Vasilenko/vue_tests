<template>
	<p>
		<ul>
			<TodoItem
				v-for = "(todoItem, i) in todoList"
				v-bind:todoItem = "todoItem"
				v-bind:key = "todoItem.id"

				v-bind:index = "i"
				v-on:todoItemRemove = "todoItemRemove"
				v-on:todoItemSaveChanges = "todoItemSaveChanges"
			/>
		</ul>
	</p>
</template>

<script>
	// импорт компонентов
	import TodoItem from '@/components/TodoItem'

	export default {
		// все входящие параметры принимаемые данным компонентом
		props: ['todoList'],
		// регистрация компонентов
		components: {
			TodoItem:TodoItem
		},
		methods: {
			todoItemRemove(todoItemId) {
				this.$emit('todoItemRemove', todoItemId)
			},
			todoItemSaveChanges(editedTodoItem){
				this.$emit('todoItemSaveChanges', editedTodoItem)
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