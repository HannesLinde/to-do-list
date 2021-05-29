<template>
  <div class="flex flex-col space-y-4">
    <h2 class="text-2xl">Create New To Do</h2>
    <form @submit.prevent="submit" class="flex flex-col space-y-2">
      <input
        type="text"
        name="title"
        placeholder="Title To Do"
        v-model="title"
        class="bg-yellow-100 text-center border border-gray-400 rounded-md"
      />
      <textarea
        name="content"
        placeholder="Content To Do"
        v-model="content"
        class="bg-yellow-100 text-center border border-gray-400 rounded-md"
        rows="5"
      />
      <div class="flex justify-center">
        <button
          type="submit"
          class="bg-yellow-500 hover:bg-yellow-100 border border-gray-200 hover:border-gray-400 rounded-md px-4"
        >
          Save
        </button>
      </div>
    </form>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import axios from "axios";
const now = new Date();

export default Vue.extend({
  data() {
    return {
      title: "",
      content: "",
    };
  },
  methods: {
    async submit() {
      console.log("submit");
      try {
        const response = await axios.post("http://localhost:3000/todos", {
          title: this.title,
          content: this.content,
          createdAt: now,
        });
        console.log(response);
        this.$router.push("/");
      } catch (error) {
        console.log("Sorry, an error occured: " + error);
      }
    },
  },
});
</script>

<style scoped>
</style>