<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue';
</script>

<template>
  <HelloWorld :numbers="[1, 2, 3]" :number-mapper="(n) => n * 2">
    <h1>Giving number mapper works</h1>
  </HelloWorld>
  <HelloWorld :numbers="[1, 2, 3]">
    <h1>The default mapper is set wrongly</h1>
  </HelloWorld>
</template>
