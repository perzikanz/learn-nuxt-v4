<script setup lang="ts">
import { ref } from 'vue'

const emit = defineEmits<{
  onSubmit: [value: string]
}>()

const text = ref("")
</script>

<template>
  <div>
    <input v-model="text" name="text"/>
    <button @click="emit('onSubmit', text)">add todo</button>
  </div>
</template>
