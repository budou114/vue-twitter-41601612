<script setup lang="ts">
import { Tweet } from '@/types/tweet';

const props = defineProps<{
  tweet: Tweet;
}>();


const emits = defineEmits<{
  (e: "delete", value: string): void;
}>();

const onDelete = (id: string) => {
  emits("delete", id);
};
</script>

<template>
  <div class="tweet">
    <span>{{ props.tweet.description }}</span>
    <button @click="() => onDelete(tweet.id)">Delete</button>
  </div>
</template>

<style scoped></style>