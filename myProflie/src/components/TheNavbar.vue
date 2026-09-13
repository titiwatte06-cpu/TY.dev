<script setup lang="ts">
import { ref } from "vue";

const isMobileMenuOpen = ref(false);

const navLinks = [
  { href: "#about", label: "About" },
  { href: "#stack", label: "Stack" },
  { href: "#projects", label: "Projects" },
  { href: "#certificates", label: "Certificates" },
];
</script>

<template>
  <nav
    class="sticky top-0 z-50 w-full border-b border-neutral-200/80 bg-neutral-50/90 backdrop-blur-md transition-colors duration-300 dark:border-neutral-800 dark:bg-neutral-950/90"
  >
    <div class="mx-auto max-w-7xl px-5 sm:px-8 lg:px-12">
      <div class="flex h-20 items-center justify-between">
        <a
          href="#"
          class="mr-auto text-3xl font-bold tracking-tight text-neutral-950 dark:text-white"
        >
          TY<span class="text-neutral-500 dark:text-neutral-400">.dev</span>
        </a>

        <div class="hidden items-center gap-7 md:flex">
          <a
            v-for="link in navLinks"
            :key="link.href"
            :href="link.href"
            class="text-xs font-semibold uppercase tracking-[0.14em] text-neutral-500 transition-colors hover:text-neutral-950 dark:text-neutral-400 dark:hover:text-white"
            >{{ link.label }}</a
          >

          <a
            href="https://github.com/titiwatte06-cpu"
            target="_blank"
            aria-label="GitHub Profile"
            class="text-lg text-neutral-500 transition-colors hover:text-neutral-950 dark:text-neutral-400 dark:hover:text-white"
          >
            <i class="fab fa-github"></i>
          </a>
        </div>

        <div class="flex items-center gap-2 md:hidden">
          <button
            type="button"
            aria-label="Toggle Navigation Menu"
            class="cursor-pointer p-2 text-neutral-600 transition-colors hover:text-neutral-950 dark:text-neutral-300 dark:hover:text-white"
            @click="isMobileMenuOpen = !isMobileMenuOpen"
          >
            <i class="fas fa-bars text-2xl"></i>
          </button>
        </div>
      </div>
    </div>

    <div
      v-if="isMobileMenuOpen"
      class="absolute w-full border-b border-neutral-200 bg-neutral-50 shadow-sm dark:border-neutral-800 dark:bg-neutral-950 md:hidden"
    >
      <div class="space-y-1 px-2 pb-3 pt-2 sm:px-3">
        <a
          v-for="link in navLinks"
          :key="link.href"
          :href="link.href"
          class="block rounded-md px-3 py-2 text-base font-medium text-neutral-700 transition-colors hover:bg-neutral-100 hover:text-neutral-950 dark:text-neutral-300 dark:hover:bg-neutral-900 dark:hover:text-white"
          >{{ link.label }}</a
        >
        <a
          href="https://github.com/weerayosong"
          target="_blank"
          class="block rounded-md px-3 py-2 text-base font-medium text-neutral-700 transition-colors hover:bg-neutral-100 hover:text-neutral-950 dark:text-neutral-300 dark:hover:bg-neutral-900 dark:hover:text-white"
        >
          <i class="fab fa-github mr-2"></i> GitHub
        </a>
      </div>
    </div>
  </nav>
</template>
