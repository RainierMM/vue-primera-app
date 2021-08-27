<template>
  <li class="list-group-item d-flex justify-content-between">
    <span role="button"> {{ countActives }} Actives </span>
    <span role="button" @click="deleteAllCompleted">
      Delete Completed
    </span>
  </li>
</template>

<script>
import { computed, inject } from "@vue/runtime-core";
export default {
  setup() {
    const todos = inject("todos");
    const countActives = computed(() => {
      return todos.value.filter((item) => item.estado === false).length;
    });

    const deleteAllCompleted = () => {
      todos.value = todos.value.filter((item) => item.estado === false);
    };

    return { countActives, deleteAllCompleted };
  },
};
</script>

<style></style>
