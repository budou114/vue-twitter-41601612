<script setup lang="ts">
import { ref } from "vue";

const tweets = ref([
  "Tweet1",
  "Tweet2",
  "Tweet3",
]);

const tweet = ref("");

const onSubmit = () => {
  tweets.value.push(tweet.value);
  tweet.value = "";
};

</script>

<template>
  <h1>Twitter</h1>
  <form @submit.prevent="onSubmit()">
    <input type="text" v-model="tweet" />
    <button type="submit">Tweet</button>
  </form>
  <ul>
    <li v-for="tweet in tweets" :key="tweet">{{ tweet }}</li>
  </ul>
</template>

<style scoped>
ul {
  list-style: none;
  padding: 0;
}

li {
  margin-top: 1rem;
}
</style>
