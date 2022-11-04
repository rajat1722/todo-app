<script setup lang="ts">
import { ref, onMounted } from "vue";
import type { TodoType } from "./types/TodoType";

const props = defineProps<{ todos: TodoType[] }>();

console.log(props.todos);

const emit = defineEmits<{
  (e: "removeTodo", todo: TodoType): void;
}>();

function removeTodo(todo: TodoType): void {
  emit("removeTodo", todo);
}
</script>

<template>
  <section class="todo-list">
    <h3>TODO LIST</h3>
    <div class="list">
      <div
        v-for="todo in props.todos"
        :key="todo.createdAt"
        :class="`todo-item ${todo.done && 'done'}`"
      >
        <label>
          <input type="checkbox" v-model="todo.done" />
          <span :class="`bubble ${todo.category}`"></span>
        </label>

        <div class="todo-content">
          <input type="text" v-model="todo.content" />
        </div>

        <div class="actions">
          <button class="delete" @click="removeTodo(todo)">Delete</button>
        </div>
      </div>
    </div>
  </section>
</template>
