<script setup lang="ts">
import { ref } from "vue";
import { Tweet } from "@/types/tweet";
import TweetComponent from "../components/Tweet.vue";
import TweetFormComponent from "../components/TweetForm.vue";

const tweets = ref<Tweet[]>([
  {
    id: "1",
    description: "Hello",
  },
  {
    id: "2",
    description: "Example",
  }
]);

const onSubmit = (description: string) => {
  tweets.value = [
    ...tweets.value,
    {
      id: Math.random().toString(),
      description,
    }
  ];
};

// const onDelete = (id: string) => {
//   tweets.value = tweets.value.filter((tweet) => tweet.id !== id);
// };
</script>

<template>
  <h1>Twitter</h1>
  <TweetFormComponent @submit="onSubmit" />

  <ul class="tweets">
    <li v-for="tweet in tweets">
      <TweetComponent :tweet="tweet" />
    </li>
  </ul>
</template>

<style scoped>
.tweet-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  textarea {
    width: 400px;
    height: 100px;
    border-radius: 4px;
  }
  button {
    width: 100px;
    height: 50px;
  }
  justify-content: center;
  align-items: center;
}

.tweets {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  height: 400px;
}

.tweet {
  background-color: #f5f5f5;
  padding: 1rem;
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
  align-items: center;

  button {
    background-color: #ff0000;
    color: #fff;
    border-radius: 4px;
    border: none;
    padding: 0.5rem;
    cursor: pointer;
  }
}

ul {
  list-style: none;
  padding: 0;
}

li {
  margin-top: 1rem;
}
</style>
