<script setup>

const userData=getUserData();

const loading=ref(false);
const config = useRuntimeConfig();

async function checkIfUserIsloggedIn() {
    try {
        const res = await $fetch(config.public?.API_BASE_URL + "/user-logged-in", {
        headers: {
            Accept: "application/json",
            "content-type": "application/json",
            Authorization: `Bearer ${userData?.token}`
        },
        method: "POST",
        });
    } catch (error) {
        loading.value = false;

        if (error?.response?.status === 401) {
        showError(error.response?._data.message);
        }
        localStorage.clear()
        navigateTo('/auth/login');
    }
}


async function logoutUser() {
  const config = useRuntimeConfig();
  try {
    loading.value = true;
    const res = await $fetch(config.public?.API_BASE_URL + "/logout", {
      headers: {
        Accept: "application/json",
        "content-type": "application/json",
        Authorization: `Bearer ${userData?.token}`
      },
      method: "POST",
      body: JSON.stringify({userData:userData?.user?.id}),
    });
    loading.value = false;

    console.log(res);
    
    successMsg(res?.message);

    localStorage.clear()

    navigateTo("/auth/login");

  } catch (error) {
    loading.value = false;

    if (error?.response?.status === 401) {
      showError(error.response?._data.message);
    }
        localStorage.clear()
        navigateTo('/auth/login');
  }
}

onMounted(async()=>{
    await checkIfUserIsloggedIn()
})
</script>
<template>
        <div class="h-screen bg-slate-100">
            <div class="pt-20 mr-28 ml-28">
                <nav class="rounded-md shadow-md flex justify-between mb-10 bg-white">
                    <Links />
                    <div class="p-2">
                        <span class="text-indigo-500" v-if="userData?.user?.email"> {{ userData?.user?.email }} - </span>
                        <button @click="logoutUser" class="p-2 rounded-full font-bold text-red-800">
                            {{ loading ? 'Processing...' : 'Logout' }}
                        </button>
                    </div>
                </nav>
                <div>
                    <slot></slot>
                </div>
            </div>
        </div>
</template>