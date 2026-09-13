<script setup lang="ts">
const currentYear = new Date().getFullYear();
</script>

<template>
  <footer
    class="border-t border-neutral-200 bg-white px-5 py-5 text-neutral-500 transition-colors duration-300 dark:border-neutral-800 dark:bg-neutral-950 dark:text-neutral-400 sm:px-8 lg:px-12"
  >
    <div
      class="mx-auto flex max-w-7xl items-center justify-center text-center text-xs"
    >
      <p>
        &copy; <span>{{ currentYear }}</span> | All rights reserved.
      </p>
    </div>
  </footer>
</template>
