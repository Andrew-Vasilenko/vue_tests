<template>
	<form v-on:submit.prevent="onSubmit">
        <input type="text" v-model = "title">
        <button type="submit">Create new Task</button>
    </form>
</template>

<script>    
    export default {
        data() {
            return {
                title: ""
            }
        },
        methods: {
            onSubmit() {
                // console.log(this.title)
                if (this.title.trim()){
                    const newTodoItem = {
                        id: Date.now(),
                        title: this.title,
                        completed: false
                    }
                    // сообщаем App компоненту об изменениях
                    this.$emit('todoItemAdd', newTodoItem)
                    this.title = ""
                }
            }
        }
    }
</script>


<style scoped>
    form {
        display: flex;
    }

    input {
        width: 100%;
    }

    button {
        background: skyblue;
		color: rgb(0, 0, 0);
		font-weight: bold;
    }
</style>