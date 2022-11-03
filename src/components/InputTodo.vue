<script setup lang="ts">
import { ref, watch } from "vue";
import type { TodoType } from "./types/TodoType";

const inputContent = ref<string>("");
const inputCategory = ref<"business" | "personal" | "">("");
const todos = ref<TodoType[]>([]);

function addTodo(): void {
  if (inputContent.value.trim() === "" || inputCategory.value === "") {
    return;
  }
  console.log("insd");
  todos.value.push({
    content: inputContent.value,
    category: inputCategory.value,
    done: false,
    createdAt: new Date().getTime(),
  });
}

watch(
  todos,
  (newTodos) => {
    localStorage.setItem("todos", JSON.stringify(newTodos));
  },
  { deep: true }
);
</script>

<template>
  <section class="create-todo">
    <h3>CREATE A TODO</h3>

    <form @submit.prevent="addTodo">
      <h4>What's on you todo list?</h4>
      <input
        type="text"
        placeholder="e.g. make a video"
        v-model="inputContent"
      />

      <h4>Pick a category</h4>

      <div class="options">
        <label>
          <input
            type="radio"
            name="category"
            value="business"
            v-model="inputCategory"
          />
          <span class="bubble business"></span>
          <div>Business</div>
        </label>
        <label>
          <input
            type="radio"
            name="category"
            value="personal"
            v-model="inputCategory"
          />
          <span class="bubble personal"></span>
          <div>Personal</div>
        </label>
      </div>

      <input type="submit" value="Add todo" />
    </form>
  </section>
</template>
