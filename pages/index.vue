<script setup>
    definePageMeta({
        layout: 'default'
    })

const articles = ref([1,2,3,4,5])
</script>

<template>
    <div>
        <div>
            <h1>List of Articles</h1>
        </div>
        
        <div v-for="(index,article) in articles" :key="index">
        <h2>Article - {{ article }}</h2>
        </div>
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestiae suscipit quis eaque quibusdam ullam, quia earum adipisci recusandae debitis hic expedita aperiam cum, doloremque, similique ducimus provident amet nobis itaque.
        </p>
    </div>
</template>