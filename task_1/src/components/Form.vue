<template>
    <div>
        <strong>{{ values[0] }}</strong>
        <strong>{{ values[1] }}</strong>
    </div>
</template>

<script>
export default{
    props: ['values']
}
</script>


<style scoped>
    div {
        display: block;
        background-color: rgb(189, 224, 238);
        margin-top: 1%;
    }

    strong {
        margin: 1%;
    }
</style>