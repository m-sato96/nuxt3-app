<script setup lang="ts">
const { counter, updateCounter } = useCounter();
</script>
<template>
  <div>
    Counter: {{ counter }}
    <button @click="updateCounter(5)">+5</button>
  </div>
</template>
