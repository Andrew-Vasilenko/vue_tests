<template>
	<li>
		<span v-bind:class = "{done: todoItem.completed}">
			<input type="checkbox"
				v-on:change = "todoItem.completed = !todoItem.completed"
			>
			<strong>{{index + 1}}. </strong>
			<span v-on:click = "toggleEditorVisibility">{{ todoItem.title }}</span>

			<form v-bind:class = "{hidden: isEditorHidden}" v-on:submit.prevent="onSubmit">
				<input type="text"
					v-model = "newTitle"
				>

				<button type="submit" class="saveChanges"
					v-bind:class = "{hidden: isEditorHidden}"
					v-on:click = "toggleEditorVisibility"
				>Save Changes</button>
			</form>
			

		</span>

		<button class="remove"
			v-bind:class = "{hidden: isEditorHidden === false}"
			v-on:click = "$emit('todoItemRemove', todoItem.id)"
		>&times;</button>

		
	</li>
</template>

<script>
export default {
	data() {
		return {
			isEditorHidden: true,
			newTitle: ""
		}
	},
	// все параметры принимаемые данным компонентом
	props: [
		'todoItem',
		'index'
	],
	methods: {
		toggleEditorVisibility(){
			this.isEditorHidden = !this.isEditorHidden
		},
		onSubmit(){
			if (this.newTitle.trim()){
				const editedTodoItem = {
					newTitle: this.newTitle,
					index: this.index
				}
				// сообщаем App компоненту об изменениях
				this.$emit('todoItemSaveChanges', editedTodoItem)
				this.newTitle = ""
			}
		}
	}
}
</script>

<style scoped>

	li {
		border: 1px solid #ccc;
		display: flex;
		justify-content: space-between;
		margin-bottom: 1%;
		padding: 1%;
	}

	.remove {
		background: red;
		color: #fff;
		border-radius: 50%;
		font-weight: bold;
	}

	.saveChanges {
		background: green;
		color: #fff;
		font-weight: bold;
		display: inline-flex;
	}

	.done {
		text-decoration: line-through;
	}

	.hidden {
		display: none;
	}

	form {
		display: inline-flex;
		margin-left: 20px;
	}
</style>