<script setup lang="ts">
import { ref } from "vue"
const todoList = ref<{ id: number; text: string }[]>([])

const handleSubmit = (text: string) => {
  const todo = { id: Date.now(), text }
  todoList.value.push(todo)
}

const handleClick = (id: number) => {
  todoList.value = todoList.value!.filter((item) => item.id !== id)
}
</script>

<template>
  <div class="container">
    <h1 class="title">TODO List</h1>
    <AddTodo @on-submit="handleSubmit" />
    <TodoList
      v-if="0 < todoList.length"
      :todo-list="todoList"
      @on-click="handleClick"
    />
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
