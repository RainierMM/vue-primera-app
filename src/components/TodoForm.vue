<template>
  <form @submit.prevent="addTodo">
    <input
      class="form-control my-3"
      placeholder="Ingrese tarea"
      v-model.trim="text"
      type="text"
    />
  </form>
</template>

<script>
import { inject, ref } from "@vue/runtime-core";
export default {
  setup() {
    const todos = inject("todos");
    const text = ref("");
    const addTodo = () => {
      if (text.value === "") {
        console.log("Está vacio");
        return;
      }
      const todo = {
        texto: text.value,
        estado: false,
        id: Date.now(),
      };
      todos.value.push(todo);
      text.value = "";
    };
    return { addTodo, text };
  },
};
</script>

<style></style>
