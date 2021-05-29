<template>
  <div class="flex flex-col space-y-8 max-w-screen-sm mx-auto">
    <router-link
      to="/create-to-do"
      class="text-2xl bg-yellow-400 rounded-xl p-8"
      >Create new To Do</router-link
    >
    <List />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import List from "@/components/List.vue";

export default Vue.extend({
  methods: {
    data() {
      return {
        id: "",
      };
    },
  },
  components: {
    List,
  },
});
</script>
