<script setup lang="ts">
import { ref } from "vue";

const isMobileMenuOpen = ref(false);
const isDark = ref(false);

function toggleTheme() {
  isDark.value = !isDark.value;
  document.documentElement.classList.toggle("dark", isDark.value);
}

const navLinks = [
  { href: "#about", label: "About" },
  { href: "#projects", label: "Projects" },
  { href: "#certificates", label: "Certificates" },
  { href: "#mini-projects", label: "Mini:p" },
  { href: "#lab", label: "Lab" },
  { href: "#saas", label: "SaaS" },
];
</script>

<template>
  <nav
    class="sticky top-0 w-full bg-white/90 dark:bg-slate-900/90 backdrop-blur-md z-50 border-b border-gray-100 dark:border-slate-800 transition-all duration-300"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center h-16">
        <a
          href="#"
          class="text-2xl font-bold text-primary dark:text-white tracking-tight"
        >
          TY<span class="text-slate-500 dark:text-slate-400">.dev</span>
        </a>

        <div class="hidden md:flex space-x-8 items-center">
          <a
            v-for="link in navLinks"
            :key="link.href"
            :href="link.href"
            class="text-sm font-semibold text-gray-600 dark:text-gray-300 hover:text-slate-900 dark:hover:text-white transition-colors"
            >{{ link.label }}</a
          >

          <a
            href="https://github.com/titiwatte06-cpu"
            target="_blank"
            aria-label="GitHub Profile"
            class="text-gray-600 dark:text-gray-300 hover:text-primary dark:hover:text-white transition-colors text-xl"
          >
            <i class="fab fa-github"></i>
          </a>

          <button
            type="button"
            aria-label="Toggle Color Theme"
            class="text-gray-500 dark:text-gray-300 hover:bg-gray-100 dark:hover:bg-slate-800 rounded-md text-sm p-2.5 cursor-pointer"
            @click="toggleTheme"
          >
            <span class="theme-icon text-xl">◾️</span>
          </button>
        </div>

        <div class="md:hidden flex items-center gap-2">
          <button
            type="button"
            aria-label="Toggle Color Theme"
            class="text-gray-700 dark:text-gray-300 hover:bg-gray-100 dark:hover:bg-slate-800 rounded-md text-sm p-2 cursor-pointer"
            @click="toggleTheme"
          >
            <span class="theme-icon text-xl">◾️</span>
          </button>
          <button
            type="button"
            aria-label="Toggle Navigation Menu"
            class="text-gray-600 dark:text-gray-300 hover:text-primary dark:hover:text-white p-2 cursor-pointer"
            @click="isMobileMenuOpen = !isMobileMenuOpen"
          >
            <i class="fas fa-bars text-2xl"></i>
          </button>
        </div>
      </div>
    </div>

    <div
      v-if="isMobileMenuOpen"
      class="md:hidden bg-white border-b dark:bg-slate-900 border-gray-100 dark:border-slate-800 absolute w-full shadow-lg"
    >
      <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
        <a
          v-for="link in navLinks"
          :key="link.href"
          :href="link.href"
          class="block px-3 py-2 rounded-md text-base font-medium text-gray-700 hover:text-slate-900 hover:bg-gray-50 dark:text-gray-300 dark:hover:text-white dark:hover:bg-slate-800"
          >{{ link.label }}</a
        >
        <a
          href="https://github.com/weerayosong"
          target="_blank"
          class="block px-3 py-2 rounded-md text-base font-medium text-gray-700 hover:text-slate-900 hover:bg-gray-50 dark:text-gray-300 dark:hover:text-white dark:hover:bg-slate-800"
        >
          <i class="fab fa-github mr-2"></i> GitHub
        </a>
      </div>
    </div>
  </nav>
</template>
