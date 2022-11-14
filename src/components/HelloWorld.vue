<script setup lang="ts">
import { ref } from 'vue';
import MyCustomModal from './MyCustomModal.vue';

export interface Props {
  numbers: number[];
  msg?: string;
}
const { numbers, msg = 'Hello World' } = defineProps<Props>();

const displayModal = ref(false);

function showModal() {
  displayModal.value = true;
}
function hideModal() {
  displayModal.value = false;
}
</script>

<template>
  <slot>
    <h1>{{ msg }}</h1>
  </slot>

  <div>
    <button @click="showModal">SHOW THE MODAL!</button>
    <Teleport to="body">
      <MyCustomModal @close="hideModal" v-if="displayModal">
        <p>Look, I am the modal content teleported to the body tag!</p>
      </MyCustomModal>
    </Teleport>
  </div>

  <div>
    <h1>Numbers For You</h1>
    <ol>
      <li v-for="n in numbers">
        {{ n }}
      </li>
    </ol>
  </div>
</template>
