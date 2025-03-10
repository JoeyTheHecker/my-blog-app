<script setup>
    definePageMeta({
        layout: 'auth'
    })

const articles = ref([1,2,3,4,5])
</script>

<template>
    <div>
        <h1>login page</h1>
        <NuxtLink to="/auth/register"> register page</NuxtLink>
    </div>
</template>