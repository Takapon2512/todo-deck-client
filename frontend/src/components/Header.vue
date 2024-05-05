<template>
  <header class="fixed h-14 w-full px-12 bg-white flex items-center justify-between text-gray-800">
    <div>
      <p class="text-xl">
        <span class="text-2xl text-red-600 font-semibold">T</span>ask <span class="text-2xl text-green-600 font-semibold">D</span>eck
      </p>
    </div>
    <ul class="flex">
      <li>
        <NuxtLink
        class="flex items-center justify-center text-sm text-center h-14 w-20 bg-red-600 text-white hover:bg-red-500 transition-all"
        to="/auth"
        >
          登録
        </NuxtLink>
      </li>
      <li>
        <NuxtLink
        class="flex items-center justify-center text-sm text-center h-14 w-20 hover:bg-neutral-100 transition-all"
        to="/auth"
        >
          ログイン
        </NuxtLink>
      </li>
    </ul>
  </header>
</template>