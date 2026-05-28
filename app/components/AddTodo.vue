<script setup lang="ts">
import { ref } from "vue"

const emit = defineEmits<{
  onSubmit: [value: string]
}>()

const text = ref("")

const handleSubmit = () => {
  emit("onSubmit", text.value)
  text.value = ""
}
</script>

<template>
  <div class="inputContainer">
    <input v-model="text" name="text" class="textInput" />
    <button @click="handleSubmit" class="addButton">add todo</button>
  </div>
</template>

<style scoped>
.inputContainer {
  display: flex;
  gap: 12px;
  width: 100%;
  height: 32px;
}

.textInput {
  width: 100%;
}

.addButton {
  width: 120px;
  background: lightseagreen;
  color: #fff;
  border: none;
  border-radius: 8px;
  &:hover {
    opacity: 0.8;
  }
}
</style>
