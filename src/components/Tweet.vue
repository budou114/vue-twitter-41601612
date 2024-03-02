<script setup lang="ts">
</script>

<template>
  <div class="tweet">
    <span>{{ tweet.description }}</span>
    <button @click="() => onDelete(tweet.id)">Delete</button>
  </div>
</template>

<style scoped></style>