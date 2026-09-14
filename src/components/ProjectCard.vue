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
    class="overflow-hidden rounded-2xl border border-neutral-200 bg-white shadow-[0_18px_50px_rgba(23,23,23,0.08)] transition-transform duration-300 hover:-translate-y-1 dark:border-neutral-800 dark:bg-neutral-900"
  >
    <div class="w-full bg-neutral-100 p-3 dark:bg-neutral-800 sm:p-5">
      <video
        v-if="screenshot"
        :src="screenshot"
        :aria-label="`${title} project preview`"
        autoplay
        loop
        muted
        playsinline
        preload="metadata"
        class="aspect-video w-full rounded-lg object-cover"
      ></video>
      <div
        v-else
        class="flex aspect-video w-full items-center justify-center rounded-lg bg-neutral-200 text-sm font-medium text-neutral-400 dark:bg-neutral-700 dark:text-neutral-500"
      >
        Coming soon
      </div>
    </div>
    <div class="min-w-0 space-y-4 p-6 sm:p-8">
      <h3
        class="text-2xl font-black tracking-tight text-neutral-950 dark:text-neutral-100 sm:text-3xl"
      >
        {{ title }}
      </h3>
      <p
        class="max-w-3xl text-base leading-7 text-neutral-600 dark:text-neutral-300"
      >
        {{ description }}
      </p>
      <p
        class="text-xs font-bold uppercase tracking-[0.14em] text-neutral-500 dark:text-neutral-400"
      >
        {{ techStack.join(", ") }}
      </p>
      <a
        :href="link"
        class="inline-flex items-center rounded-md border border-neutral-300 px-4 py-2 text-sm font-medium text-neutral-700 transition-colors hover:border-neutral-950 hover:bg-neutral-950 hover:text-white dark:border-neutral-700 dark:text-neutral-300 dark:hover:border-neutral-100 dark:hover:bg-neutral-100 dark:hover:text-neutral-950"
      >
        View project
      </a>
    </div>
  </div>
</template>
