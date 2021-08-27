<template>
  <ul class="list-group">
    <todo-entry v-for="todo in todos" :key="todos.id" :todo="todo" />
    <li class="list-group-item" v-if="todos.length === 0">
      No hay actividades
    </li>
    <todo-footer v-if="todos.length !== 0" />
    <todo-filters />
  </ul>
</template>

<script>
import { computed, inject, provide, ref } from "@vue/runtime-core";
import TodoEntry from "./TodoEntry.vue";
import TodoFooter from "./TodoFooter.vue";
import TodoFilters from "./TodoFilters.vue";
export default {
  components: { TodoEntry, TodoFooter, TodoFilters },

  setup() {
    const todosAll = inject("todos");

    const state = ref("all");

    const todos = computed(() => {
      if (state.value === "all") {
        return todosAll.value;
      }
      if (state.value === "actives") {
        return todosAll.value.filter((item) => item.estado === false);
      }

      if (state.value === "completed") {
        return todosAll.value.filter((item) => item.estado === true);
      }
    });

    provide("state", state);

    return { todos };
  },
};
</script>

<style></style>
