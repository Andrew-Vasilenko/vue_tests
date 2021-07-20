<template>
    <div>
        <h3
            v-on:click = "toggleFormVisibility"
        >{{ serverResponse.title }}</h3>
        <Form
            v-bind:values = "serverResponse.values"
            v-bind:class = "{hidden: isHidden}"
        />
    </div>    
</template>

<script>
import Form from "@/components/Form"

export default {
    data () {
        return {
            isHidden: false
        }
    },
    props: ['serverResponse'],
    components: {
        Form:Form
    },
    methods: {
        toggleFormVisibility() {
            this.isHidden = !this.isHidden
        }
    }
}
</script>

<style scoped>
    .hidden {
        display: none;
    }
</style>>