<template>
  <div>
    <Group
      v-for = "arrElement in serverResponses"
      v-bind:serverResponse = "arrElement"
      v-bind:key = "arrElement.values"
    />
  </div>
</template>

<script>
import Group from "@/components/FormElements/Group"

export default {
  name: 'App',
  data () {
    return {
      serverResponses: [
        { title: "Заголовок1", values: ["<сложные аббревиатуры>", "Полное наименование"] },
        { title: "Заголовок2", values: ["<сложные аббревиатуры>", "Полное наименование"] }
      ]
    }
  },
  components: {
    Group:Group
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
