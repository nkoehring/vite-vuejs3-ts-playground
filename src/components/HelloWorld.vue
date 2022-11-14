<script setup lang="ts">
import { ref } from 'vue';
import MyCustomModal from './MyCustomModal.vue';
import { noop } from '../util';

export interface Props {
  numbers: number[];
  numberMapper: (n: number) => n;
  msg?: string;
}
const {
  numbers,
  numberMapper = noop,
  msg = 'Hello World',
} = defineProps<Props>();

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
    <p>Numbers For You:</p>
    <ol>
      <li v-for="n in numbers">
        {{ numberMapper(n) }}
      </li>
    </ol>
  </div>
</template>
