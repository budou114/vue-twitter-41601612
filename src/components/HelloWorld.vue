<script setup lang="ts">
import { ref } from "vue";

type Tweet = {
  id: string;
  description: string;
}

const tweets = ref<Tweet[]>([
  {
    id: "1",
    description: "Hello World1",
  },
  {
    id: "2",
    description: "Hello World2",
  }
]);

const tweet = ref<Tweet>({
  id: "",
  description: ""
});

const onSubmit = () => {
  tweets.value = [
    ...tweets.value,
    {
      id: Math.random.toString(),
      description: tweet.value.description,
    }
  ];

  tweet.value = {
    id: "",
    description: ""
  };
};

const onDelete = (id: string) => {
  tweets.value = tweets.value.filter((tweet) => tweet.id !== id);
}

</script>

<template>
  <h1>Twitter</h1>
  <form @submit.prevent="onSubmit()">
    <input type="text" v-model="tweet.description" />
    <button type="submit">Tweet</button>
  </form>
  <ul>
    <li v-for="tweet in tweets" :key="tweet.id">
      <div>
        <span>{{ tweet.description }}</span>
        <button @click="() => onDelete(tweet.id)">Delete</button>
      </div>
    </li>
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
