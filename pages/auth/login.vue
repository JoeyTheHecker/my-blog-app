<script setup>
    definePageMeta({
        layout: 'auth'
    })

const articles = ref([1,2,3,4,5])
</script>

<template>
    <div class="bg-slate-100">
        <div></div>
        <div class="w-[300px] mt-20">
            <div class="flex flex-col gap-2">
                <h1 class="text-2x1">Login</h1>
                <input type="text" name="" placeholder="E-mail" id=""
                class="py-2 px-2 text-sm rounded-md shadow-sm focus:ring focus:ring-blue-300">
                <input type="password" name="" placeholder="E-mail" id=""
                class="py-2 px-2 text-sm rounded-md shadow-sm focus:ring focus:ring-blue-300">
                <button class="rounded-md text-indigo-700 text-sm font-semibold">Login</button>
            </div>
        </div>
    </div>
</template>