<template>
  <div class="flex flex-col space-y-4">
    <h2 class="text-2xl">All my To Dos</h2>
    <div v-if="todos.length == 0">Nothing to do. Whooohooo!</div>
    <div
      v-for="todo in todos"
      :key="todo.id"
      class="flex flex-col space-y-2 bg-green-400 border border-gray-400 p-4 rounded-xl"
    >
      <div class="flex justify-between">
        <div class="text-xl">{{ todo.title }}</div>
        <div class="text-gray-800 text-sm">
          {{ new Date(todo.createdAt).toLocaleDateString() }}
        </div>
      </div>
      <hr />
      <div>{{ todo.content }}</div>
      <div class="flex justify-end">
        <button
          @click="deleteToDo"
          class="bg-pink-400 hover:bg-pink-100 border border-black rounded-md px-2"
        >
          Delete this To Do
        </button>
      </div>
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
    this.listToDos();
  },
  methods: {
    async listToDos() {
      const response = await axios.get("http://localhost:3000/todos");
      this.todos = response.data;
      console.log(response.data);
    },
    async deleteToDo() {
      const id = 1;
      const response = await axios.delete(
        "http://localhost:3000/todos/" + `${id}`
      );
      console.log(response);
      return "Message deleted";
    },
    log() {
      console.log(this.todos);
    },
  },
});
</script>

<style scoped>
</style>