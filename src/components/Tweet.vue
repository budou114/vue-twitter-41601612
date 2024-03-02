<script setup lang="ts">
import { Tweet } from '@/types/tweet';

const props = defineProps<{
  tweet: Tweet;
}>();
</script>

<template>
  <div class="tweet">
    <span>{{ props.tweet.description }}</span>
    <!-- <button @click="() => onDelete(tweet.id)">Delete</button> -->
  </div>
</template>

<style scoped></style>