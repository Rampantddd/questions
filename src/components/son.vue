<script lang="ts" setup>
import EventBus from "../common"

defineProps<{
  modelValue: string
}>()

const emit = defineEmits<{
  (e: 'update:modelValue', res: string): void
}>()

const emitMes = () => {
  emit('update:modelValue', 'my son')
}

const setBoter = () => {
  EventBus.emit("click", "兄弟通信")
}
</script>

<template>
  <h1>{{ modelValue }}</h1>
  <button @click="emitMes()">改变</button>
  <button @click="setBoter">兄弟传参</button>
</template>

<style scoped></style>