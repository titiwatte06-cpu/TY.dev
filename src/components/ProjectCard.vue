<!-- ProjectCard.vue -->
<script setup lang="ts">
defineProps<{
  title: string;
  description: string;
  techStack: string[];
  link: string;
  screenshot?: string;
  accentColor?: string;
  reversed?: boolean;
}>();
</script>

<template>
  <div
    class="flex gap-8 items-center"
    :class="reversed ? 'flex-row-reverse' : ''"
  >
    <div
      class="flex-[0_0_42%] bg-neutral-50 dark:bg-neutral-800 rounded-xl p-3"
    >
      <video
        v-if="screenshot"
        :src="screenshot"
        autoplay
        loop
        muted
        playsinline
        class="w-full h-auto object-cover"
      ></video>
      <div
        v-else
        class="w-full aspect-video flex items-center justify-center text-neutral-400 dark:text-neutral-500 text-sm font-medium"
      >
        Coming soon
      </div>
    </div>
    <div class="flex-1">
      <p class="text-base font-bold text-neutral-950 dark:text-neutral-100">
        {{ title }}
      </p>
      <p class="text-sm text-neutral-600 dark:text-neutral-300">
        {{ description }}
      </p>
      <p class="text-sm text-neutral-500 dark:text-neutral-400">
        {{ techStack.join(", ") }}
      </p>
      <a
        :href="link"
        class="mt-3 inline-flex items-center rounded-md border border-neutral-300 px-4 py-2 text-sm font-medium text-neutral-700 transition-colors hover:border-neutral-950 hover:bg-neutral-950 hover:text-white dark:border-neutral-700 dark:text-neutral-300 dark:hover:border-neutral-100 dark:hover:bg-neutral-100 dark:hover:text-neutral-950"
      >
        View project
      </a>
    </div>
  </div>
</template>
