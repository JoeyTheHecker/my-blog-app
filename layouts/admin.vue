<template>
    <nav class="rounded-md shadow-md flex justify-between mb-10 bg-white">
          <Links />
          <div class="p-2">
              <button class="p-2 rounded-full font-bold text-red-800">
                Logout
              </button>
          </div>
        </nav>

      <div>
        <div class="mr-28 ml-28">
          <slot></slot>
        </div>
      </div>
</template>