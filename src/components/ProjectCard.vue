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
    class="overflow-hidden rounded-xl border border-neutral-200 bg-white shadow-[0_12px_36px_rgba(23,23,23,0.06)] transition-transform duration-300 hover:-translate-y-1 dark:border-neutral-800 dark:bg-neutral-900"
  >
    <div class="bg-neutral-100 p-3 dark:bg-neutral-800 sm:p-5">
      <video
        v-if="screenshot"
        :src="screenshot"
        :aria-label="`${title} project preview`"
        autoplay
        loop
        muted
        playsinline
        preload="metadata"
        class="aspect-video w-full rounded-md object-cover shadow-sm"
      ></video>
      <div
        v-else
        class="flex aspect-video w-full items-center justify-center rounded-md bg-neutral-200 text-sm font-medium text-neutral-400 dark:bg-neutral-700 dark:text-neutral-500"
      >
        Coming soon
      </div>
    </div>
    <div
      class="grid gap-8 p-6 sm:p-8 lg:grid-cols-[minmax(0,1fr)_230px] lg:gap-12 lg:p-10"
    >
      <div>
        <h3
          class="text-2xl font-black leading-tight tracking-tight text-neutral-950 dark:text-neutral-100 sm:text-4xl"
        >
          {{ title }}
        </h3>
        <p
          class="mt-5 text-sm leading-7 text-neutral-600 dark:text-neutral-300 sm:text-base"
        >
          {{ description }}
        </p>
      </div>
      <div class="flex flex-col items-start gap-7 lg:pt-1">
        <div class="flex flex-wrap gap-2">
          <span
            v-for="technology in techStack"
            :key="technology"
            class="rounded-md border border-neutral-200 bg-neutral-50 px-3 py-2 text-[10px] font-bold uppercase tracking-[0.12em] text-neutral-500 dark:border-neutral-700 dark:bg-neutral-800 dark:text-neutral-300"
          >
            {{ technology }}
          </span>
        </div>
        <a
          :href="link"
          class="text-sm font-bold text-neutral-700 underline decoration-neutral-300 underline-offset-4 transition-colors hover:text-neutral-950 dark:text-neutral-300 dark:decoration-neutral-600 dark:hover:text-white"
        >
          View project
        </a>
      </div>
    </div>
  </div>
</template>
