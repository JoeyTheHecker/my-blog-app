<script setup>
definePageMeta({
  layout: "auth",
});
const registerInput = ref({
  name: "",
  email: "",
  password: "",
});

const loading = ref(false);
const config = useRuntimeConfig();

async function createUser() {
  try {
    loading.value = true;
    const res = await $fetch(config.public?.API_BASE_URL + "/register", {
      headers: {
        Accept: "application/json",
        "content-type": "application/json",
      },
      method: "POST",
      body: JSON.stringify(registerInput.value),
    });
    loading.value = false;
    console.log(res);
    successMsg(res?.message);
  } catch (error) {
    loading.value = false;
    if (error?.response?.status === 422) {
      const errors = error.response?._data;
      for (const message of errors) {
        showError(message);
      }
    }
  }
}
</script>

<template>
  <div class="bg-slate-100 h-screen">
    <div class="flex justify-between">
      <div></div>
      <div class="w-[300px] mt-20">
        <div class="flex flex-col gap-2">
          <h1 class="text-2x1">Register</h1>
          <input
            v-model="registerInput.name"
            type="text"
            name="name"
            placeholder="Name"
            id="name"
            class="py-2 px-2 text-sm rounded-md shadow-sm focus:ring focus:ring-blue-300"
          />
          <input
            v-model="registerInput.email"
            type="text"
            name="email"
            placeholder="E-mail"
            id="email"
            class="py-2 px-2 text-sm rounded-md shadow-sm focus:ring focus:ring-blue-300"
          />
          <input
            v-model="registerInput.password"
            type="password"
            name="password"
            placeholder="Password"
            id="password"
            class="py-2 px-2 text-sm rounded-md shadow-sm focus:ring focus:ring-blue-300"
          />
          <NuxtLink to="/auth/login" class="text-indigo-700 font-semibold">
            Login
          </NuxtLink>
          <button
            @click="createUser"
            :disabled="loading"
            class="rounded-md text-white bg-indigo-700 py-2 text-sm font-semibold"
          >
            {{ loading ? "Processing..." : "Create an Account" }}
          </button>
        </div>
      </div>
      <div></div>
    </div>
  </div>
</template>
