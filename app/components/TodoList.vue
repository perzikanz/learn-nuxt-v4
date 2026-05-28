<script setup lang="ts">
const { todoList } = defineProps<{
  todoList: { id: number; text: string }[]
}>()
const emit = defineEmits<{
  onClick: [value: number]
}>()
</script>

<template>
  <ul class="list">
    <li v-for="item in todoList" :key="item.id" class="listItem">
      <button @click="emit('onClick', item.id)" class="doneButton">✓</button>
      <p class="itemText">{{ item.text }}</p>
    </li>
  </ul>
</template>

<style>
.list {
  display: flex;
  flex-direction: column;
  gap: 12px;
  list-style: none;
  padding: 0;
  margin-top: 32px;
}

.listItem {
  --list-item-height: 32px;
  display: flex;
  gap: 8px;
  height: var(--list-item-height);
}

.doneButton {
  background: none;
  border: 1px solid lightseagreen;
  border-radius: 8px;
  height: 100%;
  aspect-ratio: 1 / 1;
  &:hover {
    background: lightseagreen;
    color: white;
  }
}

.itemText {
  height: 100%;
  line-height: var(--list-item-height);
  margin: 0;
}
</style>
