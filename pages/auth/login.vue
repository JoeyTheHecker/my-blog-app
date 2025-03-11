<script setup>
    definePageMeta({
        layout: 'auth'
    })

    const loginInput=ref({
    email:'',
    password:''
    })
</script>

<template>
    <div class="bg-slate-100 h-screen">
        <div class="flex justify-between">
            <div></div>
            <div class="w-[300px] mt-20">
                <div class="flex flex-col gap-2">
                    <h1 class="text-2x1">Login</h1>
                    <input v-model="loginInput.email" type="text" name="" placeholder="E-mail" id=""
                    class="py-2 px-2 text-sm rounded-md shadow-sm focus:ring focus:ring-blue-300">
                    <input v-model="loginInput.password" type="password" name="" placeholder="Password" id=""
                    class="py-2 px-2 text-sm rounded-md shadow-sm focus:ring focus:ring-blue-300">
                    <NuxtLink to="/auth/register" class="text-indigo-700 font-semibold">
                        create an acount
                    </NuxtLink>
                    <button class="rounded-md text-white bg-indigo-700 py-2 text-sm font-semibold">Login</button>
                </div> 
            </div>
            <div></div>
        </div>
    </div>
</template>