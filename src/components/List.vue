<template>
  <div class="flex flex-col place-items-center space-y-4">
    <h2 class="text-2xl">Open To Dos</h2>
    <div v-if="todos.length == 0">Nothing to do. Whooohooo!</div>
    <div
      v-for="todo in todos"
      :key="todo.id"
      class="flex flex-col w-full space-y-2 bg-green-400 border border-gray-400 p-4 rounded-xl"
    >
      <div
        v-if="deletionConfirmation"
        class="bg-red-400 cursor-pointer"
        @click="deleteToDo()"
      >
        Click here to confirm deletion.
      </div>
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
          @click="setIdAndDelete(todo)"
          class="bg-pink-400 hover:bg-pink-100 border border-black rounded-md px-2"
        >
          Done/Delete
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="">
import Vue from "vue";
import axios from "axios";

export default Vue.extend({
  data() {
    return {
      todos: [],
      selectedToDo: { id: -1 },
      deletionConfirmation: false,
    };
  },
  async mounted() {
    this.listToDos();
  },
  computed: {
    computeDeletion() {
      this.deleteToDo();
      return this.todos;
    },
  },
  methods: {
    async listToDos() {
      const response = await axios.get("http://localhost:3000/todos");
      this.todos = response.data;
      console.log(response.data);
    },
    setIdAndDelete(todo) {
      this.selectedToDo.id = todo.id;
      console.log(this.selectedToDo.id);
      this.deleteToDo();
    },
    async deleteToDo() {
      const response = await axios.delete(
        "http://localhost:3000/todos/" + `${this.selectedToDo.id}`
      );
      console.log(response);
    },
  },
});
</script>

<style scoped>
</style>