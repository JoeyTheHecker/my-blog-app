<script setup>
definePageMeta({
  layout: "auth",
});

const loginInput = ref({
  email: "admin@y.com",
  password: "123456789",
});

const loading = ref(false);

async function loginUser() {
  const config = useRuntimeConfig();
  try {
    loading.value = true;
    const res = await $fetch(config.public?.API_BASE_URL + "/login", {
      headers: {
        Accept: "application/json",
        "content-type": "application/json",
      },
      method: "POST",
      body: JSON.stringify(loginInput.value),
    });
    loading.value = false;
    console.log(res);
    // successMsg(res?.message);

    localStorage.setItem(
      "userData",
      JSON.stringify({
        user: res?.user,
        token: res?.token,
      })
    );

    navigateTo("/admin/dashboard");
  } catch (error) {
    loading.value = false;

    if (error?.response?.status === 401) {
      showError(error.response?._data.message);
    }

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
          <h1 class="text-2x1">Login</h1>
          <input
            v-model="loginInput.email"
            type="text"
            name=""
            placeholder="E-mail"
            id=""
            class="py-2 px-2 text-sm rounded-md shadow-sm focus:ring focus:ring-blue-300"
          />
          <input
            v-model="loginInput.password"
            type="password"
            name=""
            placeholder="Password"
            id=""
            class="py-2 px-2 text-sm rounded-md shadow-sm focus:ring focus:ring-blue-300"
          />
          <NuxtLink to="/auth/register" class="text-indigo-700 font-semibold">
            create an acount
          </NuxtLink>
          <button
            @click="loginUser"
            :disabled="loading"
            class="rounded-md text-white bg-indigo-700 py-2 text-sm font-semibold"
          >
            {{ loading ? "Processing..." : "Login" }}
          </button>
        </div>
      </div>
      <div></div>
    </div>
  </div>
</template>
