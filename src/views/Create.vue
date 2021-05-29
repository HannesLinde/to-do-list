<template>
  <div class="relative max-w-screen-sm mx-auto my-4">
    <BackToList />
    <Form />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Form from "@/components/Form.vue";
import BackToList from "@/components/BackToList.vue";

export default Vue.extend({
  components: {
    Form,
    BackToList,
  },
});
</script>

<style scoped>
</style>