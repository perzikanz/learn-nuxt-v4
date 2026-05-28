<script setup lang="ts">
import { ref } from "vue"
const todoList = ref<null | { id: number; text: string }[]>(null)

const handleSubmit = (text: string) => {
  const todo = { id: Date.now(), text }
  if (todoList.value) {
    todoList.value.push(todo)
    return
  }

  todoList.value = [todo]
}
</script>

<template>
  <div class="container">
    <h1 class="title">TODO List</h1>
    <AddTodo @on-submit="handleSubmit" />
    <ul v-if="todoList">
      <li v-for="item in todoList" :key="item.id">
        {{ item.text }}
      </li>
    </ul>
  </div>
</template>

<style scoped>
.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 2rem;
}

.title {
  color: darkslategray;
}
</style>
