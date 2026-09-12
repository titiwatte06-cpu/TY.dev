<!-- src/components/ProjectCardSkeleton.vue -->
<script setup lang="ts">
defineProps<{ reversed?: boolean }>();
</script>

<template>
  <div
    class="flex gap-8 items-center animate-pulse"
    :class="reversed ? 'flex-row-reverse' : ''"
  >
    <div class="flex-[0_0_42%] h-40 rounded-xl bg-neutral-800"></div>
    <div class="flex-1 flex flex-col gap-3">
      <div class="h-4 w-1/2 rounded bg-neutral-800"></div>
      <div class="h-2.5 w-11/12 rounded bg-neutral-800"></div>
      <div class="h-2.5 w-3/4 rounded bg-neutral-800"></div>
      <div class="h-2.5 w-1/3 rounded bg-neutral-800 mt-1"></div>
      <div class="h-8 w-28 rounded bg-neutral-800 mt-2"></div>
    </div>
  </div>
</template>
