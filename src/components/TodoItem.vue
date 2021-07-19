<template>
	<li>
		<span v-bind:class = "{done: todoItem.completed}">
			<input type="checkbox"
				v-on:change = "todoItem.completed = !todoItem.completed"
			>
			<strong>{{index + 1}}</strong>
			{{ todoItem.title }}
		</span>
		<button class="remove"
			v-on:click = "$emit('todoItemRemove', todoItem.id)"
		>&times;</button>
	</li>
</template>

<script>
export default {
	// все параметры принимаемые данным компонентом
	props: [
		'todoItem',
		'index'
	]
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

	.done {
		text-decoration: line-through;
	}
</style>