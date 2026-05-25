<script setup lang="ts">
import { ref } from 'vue'
const todoList = ref<null|{id:number,text:string}[]>(null)

const handleSubmit = (text:string)=>{
  const todo = {id: Date.now(), text}
  if(todoList.value){
    todoList.value.push(todo)
    return
  }

  todoList.value = [todo]
}
</script>


<template>
  <div>
    <h1>TODO List</h1>
    <AddTodo @on-submit="handleSubmit" />
    <ul v-if="todoList">
      <li v-for="item in todoList" :key="item.id">
        {{ item.text }}
      </li>
    </ul>
  </div>
</template>
