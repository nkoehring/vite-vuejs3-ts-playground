<script setup lang="ts">
export interface Props {
  title?: string;
}

const emit = defineEmits(['close']);
const { title = 'Teleported Modal' } = defineProps<Props>();
</script>

<template>
  <div class="modal">
    <h2>{{ title }}</h2>
    <slot></slot>
    <button @click="emit('close')">CLOSE ME</button>
  </div>
</template>

<style scoped>
.modal {
  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(235, 235, 241, 0.8);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
