<template>
  <div class="card mt-3">
    <div class="card-body d-flex justify-content-between">
      <span role="button" @click="filter('actives')">Actives</span>
      <span role="button" @click="filter('all')">All</span>
      <span role="button" @click="filter('completed')">Completed</span>
    </div>
  </div>
</template>

<script>
import { inject } from "@vue/runtime-core";
export default {
  setup() {
    const state = inject("state");

    const filter = (string) => {
      state.value = string;
    };

    return { filter };
  },
};
</script>

<style></style>
