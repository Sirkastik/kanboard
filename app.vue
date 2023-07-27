<template>
  <div class="max-w-[90vw] mx-auto min-h-screen flex flex-col">
    <header
      class="flex justify-center items-center px-4 py-4 my-12 uppercase font-bold text-lg"
    >
      Welcome to your Kanboard Manager
    </header>

    <NuxtPage />

    <footer class="mt-5 py-4 text-center">
      <span class="text-sm">
        &copy; Kanboard <span> • {{ new Date().getFullYear() }}</span>
      </span>
    </footer>
  </div>
</template>
