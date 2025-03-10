<script setup>
    definePageMeta({
        layout: 'auth'
    })

const articles = ref([1,2,3,4,5])
</script>

<template>
    <div>
        <h1>register page</h1>
        <NuxtLink to="/admin/dashboard">Move to dashboard</NuxtLink>
    </div>
</template>