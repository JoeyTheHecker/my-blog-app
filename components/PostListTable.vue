
<script setup>

defineProps({ posts: Array });

</script>


<template>
    <div>
      <h1 class="text-2x1 mb-2">Post-list</h1>
      <div class="flex justify-between mb-2">
        <input
          placeholder="Search..."
          type="text"
          class="mb-2 border rounded-md py-1 px-2 shadow-md"
        />
        <NuxtLink to="/admin/create-post"
          class="rounded-md text-white px-2 py-2 bg-indigo-700 text-sm font-semibold"
        >
          Create a Post
      </NuxtLink>
      </div>
  
      <table class="bg-white rounded-md w-full shadow-md border border-gray-300">
        <thead>
          <tr class="bg-gray-100 text-left">
            <td class="border border-gray-300 py-2 px-4">Image</td>
            <td class="border border-gray-300 py-2 px-4">Post-Title</td>
            <td class="border border-gray-300 py-2 px-4">Upload</td>
            <td class="border border-gray-300 py-2 px-4">Edit</td>
            <td class="border border-gray-300 py-2 px-4">Delete</td>
          </tr>
        </thead>
  
        <tbody>
          <tr class="text-left" v-for="post in posts" :key="post?.id">
            <td class="border border-gray-300 py-2 px-4">
               <img :src="post?.image" width="150"/>
            </td>

            <td class="border border-gray-300 py-2 px-4">
                {{ post?.title }}
            </td>

            <td class="border border-gray-300 py-2 px-4">
            </td>

            <td class="border border-gray-300 py-2 px-4">
            </td>
            <td class="border border-gray-300 py-2 px-4">
            </td>
            
          </tr>
        </tbody>
      </table>
    </div>
  </template>