<script setup>
import { computed } from "vue";
import { TailwindPagination } from 'laravel-vue-pagination';

  definePageMeta({
    layout: "admin",
  });

  const userData = getUserData();
  const config = useRuntimeConfig();
  const query = ref('');
  const page=ref(1);

  const { data, error, status, refresh } = await useFetch(config.public?.API_BASE_URL + "/posts", {
    headers: {
      Accept: "application/json",
      Authorization: `Bearer ${userData?.token}`,
    },
    watch:[query,page],
    query:{
        query:query,
        page:page
    }
});

  function _debounce(cb,delay){
    let timer

    return function(...args){
      clearTimeout(timer)
      timer = setTimeout(()=> cb(args),delay)
    }
  }

  const searchPost = _debounce(function(searchVal){
      console.log(searchVal);
      query.value==searchVal[0];
  })

  const paginateData = async (newPageVal) => {
      page.value = newPageVal
      await refresh()
  }

const posts = computed(() => data.value?.data?.data || []);
</script>

<template>
  <div>
    <h1 class="text-2xl mb-2">Post List</h1>

    <PostListTable @searchPost="searchPost" :posts="posts" :status="status"/>
    
    <TailwindPagination
        :data="posts"
        @pagination-change-page="paginateData"
    />

  </div>
</template>
