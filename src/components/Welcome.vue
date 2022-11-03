<script setup lang="ts">
import {ref, onMounted, computed, watch} from "vue"

const name = ref<string>("");

watch(name, (newName) => {
  localStorage.setItem("name", newName);
})

onMounted(() => {
  name.value = localStorage.getItem("name") || "";
})
</script>

<template>
  <section class="greeting">
    <h2 class="title">
      What's up, <input type="text" placeholder="Name here" v-model="name" />
    </h2>
  </section>
</template>
