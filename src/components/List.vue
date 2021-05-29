<template>
  <div>
    <h2 class="text-2xl">All my To Dos</h2>
    <div v-if="todos.length == 0">Nothing to do. Whooohooo!</div>
    <div v-for="todo in todos" :key="todo.id">
      <div class="text-xl">{{ todo.title }}</div>
      <div>{{ todo.content }}</div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import axios from "axios";

export default Vue.extend({
  data() {
    return {
      todos: [],
    };
  },
  async mounted() {
    console.log("load list");
    this.listToDos();
  },
  methods: {
    async listToDos() {
      const response = await axios.get("http://localhost:3000/todos");
      this.todos = response.data;
      console.log(response.data);
    },
  },
});
</script>

<style scoped>
</style>