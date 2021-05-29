<template>
  <div class="home">
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
