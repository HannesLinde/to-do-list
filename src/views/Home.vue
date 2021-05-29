<template>
  <div class="flex flex-col space-y-8 max-w-screen-sm mx-auto">
    <Form />
    <List />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import axios from "axios";
import Form from "@/components/Form.vue";
import List from "@/components/List.vue";

export default Vue.extend({
  methods: {
    data() {
      return {
        id: "",
      };
    },
    /* async deleteToDo() {
      const response = await axios.delete(
        "http://localhost:3000/todos/" + `${this.id}`
      );
      console.log(response);
      return "Message deleted";
    }, */
  },
  components: {
    Form,
    List,
  },
});
</script>
