<template>
  <div class="flex flex-col space-y-8 max-w-screen-sm mx-auto">
    <Form />
    <List />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Form from "@/components/Form.vue";
import List from "@/components/List.vue";

@Component({
  components: {
    Form,
    List,
  },
})
export default class Home extends Vue {}
</script>
