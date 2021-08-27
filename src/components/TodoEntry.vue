<template>
  <li class="list-group-item d-flex justify-content-between">
    <span
      role="button"
      @click="completedState(todo.id)"
      :class="{ completed: todo.estado }"
    >
      {{ todo.texto }}
    </span>
    <span role="button" @click="deleteItem(todo.id)">
      <i class="fas fa-times"></i>
    </span>
  </li>
</template>

<script>
import { inject } from "@vue/runtime-core";
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },

  setup() {
    const todos = inject("todos");

    const deleteItem = (id) => {
      todos.value = todos.value.filter((item) => item.id !== id);
    };

    const completedState = (id) => {
      todos.value = todos.value.map((item) => {
        if (item.id === id) {
          if (item.estado === false) {
            item.estado = true;
          } else {
            item.estado = false;
          }
        }

        return item;
      });
    };

    return { deleteItem, completedState };
  },
};
</script>

<style>
.completed {
  text-decoration: line-through;
}
</style>
