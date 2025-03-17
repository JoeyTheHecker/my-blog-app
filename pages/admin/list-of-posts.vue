<script setup>
import { computed } from "vue";

definePageMeta({
  layout: "admin",
});

const userData = getUserData();
const config = useRuntimeConfig();

const { data, error, status } = await useFetch(config.public?.API_BASE_URL + "/posts", {
  headers: {
    Accept: "application/json",
    Authorization: `Bearer ${userData?.token}`,
  },
  method: "GET",
});

// Extract the posts array correctly
const posts = computed(() => data.value?.data?.data || []);
</script>

<template>
  <div>
    <h1 class="text-2xl mb-2">Post List</h1>


    <PostListTable :posts="posts" :status="status"/>
  </div>
</template>
