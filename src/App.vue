<script setup lang="ts">
import {ref, onMounted, computed, watch} from "vue"
import Welcome from "./components/Welcome.vue"
import InputTodo from "./components/InputTodo.vue";

</script>

<template>
  <main class="app">
    <Welcome />
    <InputTodo />
  </main>
</template>
