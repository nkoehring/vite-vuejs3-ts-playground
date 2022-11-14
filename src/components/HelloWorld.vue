<script setup type="ts">
import { ref } from 'vue';
import MyCustomModal from './MyCustomModal.vue';

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
    <h3>{{ msg }}</h3>
  </slot>

  <div class="trigger-modal">
    <button @click="showModal">SHOW THE MODAL!</button>
    <Teleport to="body">
      <MyCustomModal @close="hideModal" v-if="displayModal">
        <p>Look, I am the modal content teleported to the body tag!</p>
      </MyCustomModal>
    </Teleport>
  </div>
</template>
