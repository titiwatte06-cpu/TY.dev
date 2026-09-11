<script setup lang="ts">
interface SocialLink {
  label: string;
  href: string;
}

interface Props {
  name: string;
  role: string;
  description: string;
  profileImage: string;
  socialLinks: SocialLink[];
}

defineProps<Props>();

const currentYear = new Date().getFullYear();

const decorativeMarks = [
  "left-[8%] top-[19%]",
  "right-[10%] top-[14%]",
  "left-[16%] bottom-[17%]",
  "right-[21%] bottom-[10%]",
  "right-[4%] top-1/2",
];

const menuItems = ["HOME", "ABOUT", "WORKS", "CONTACT"];
</script>

<template>
  <section
    class="relative isolate min-h-screen overflow-hidden bg-gray-50 px-5 py-8 text-gray-950 sm:px-8 lg:px-12"
  >
    <div
      aria-hidden="true"
      class="pointer-events-none absolute inset-0 -z-10 opacity-60 [background-image:linear-gradient(to_right,rgba(17,24,39,0.045)_1px,transparent_1px),linear-gradient(to_bottom,rgba(17,24,39,0.045)_1px,transparent_1px)] [background-size:48px_48px]"
    ></div>

    <span
      v-for="mark in decorativeMarks"
      :key="mark"
      aria-hidden="true"
      :class="[
        'absolute z-0 select-none text-xl font-light text-gray-300',
        mark,
      ]"
      >+</span
    >

    <div
      class="mx-auto flex min-h-[calc(100vh-4rem)] max-w-6xl flex-col justify-center"
    >
      <p
        class="mb-5 text-[10px] font-medium tracking-[0.32em] text-gray-500 sm:text-xs"
      >
        WEB DESIGN / UI / UX
        <span class="ml-2 text-gray-400">{{ currentYear }}</span>
      </p>

      <div class="relative">
        <div
          aria-hidden="true"
          class="absolute left-1/2 top-1/2 -z-10 aspect-square w-[min(78vw,34rem)] -translate-x-1/2 -translate-y-1/2 rounded-full bg-gradient-to-br from-gray-200 via-gray-100 to-white blur-2xl"
        ></div>

        <article
          class="relative grid overflow-hidden rounded-3xl border border-gray-900/15 bg-white shadow-[0_20px_70px_rgba(17,24,39,0.08)] md:grid-cols-[1.1fr_0.9fr]"
        >
          <div class="flex min-h-[38rem] flex-col p-6 sm:p-9 lg:p-12">
            <nav
              class="flex items-center justify-between gap-5"
              aria-label="Main navigation"
            >
              <a
                href="#"
                aria-label="Home"
                class="flex h-8 w-8 shrink-0 items-center justify-center rounded-full border border-gray-950 text-[9px] font-bold tracking-tight transition-colors hover:bg-gray-950 hover:text-white"
              >
                {{ name.slice(0, 2).toUpperCase() }}
              </a>

              <div
                class="flex items-center gap-3 text-[9px] font-semibold tracking-[0.13em] text-gray-500 sm:gap-6 sm:text-[10px]"
              >
                <a
                  v-for="(item, index) in menuItems"
                  :key="item"
                  :href="index === 0 ? '#' : `#${item.toLowerCase()}`"
                  :class="[
                    'relative py-2 transition-colors hover:text-gray-950',
                    index === 0
                      ? 'text-gray-950 after:absolute after:-bottom-0.5 after:left-1/2 after:h-1 after:w-1 after:-translate-x-1/2 after:rounded-full after:bg-gray-950'
                      : '',
                  ]"
                >
                  {{ item }}
                </a>
              </div>
            </nav>

            <div class="my-auto max-w-xl py-16 md:py-20">
              <p
                class="mb-5 text-xs font-semibold uppercase tracking-[0.26em] text-gray-400"
              >
                {{ role }}
              </p>
              <h1
                class="max-w-lg text-5xl font-black leading-[0.96] tracking-[-0.05em] sm:text-7xl"
              >
                {{ name }}
              </h1>
              <p class="mt-7 max-w-md text-sm leading-7 text-gray-500">
                {{ description }}
              </p>
              <a
                href="#works"
                aria-label="View works"
                class="mt-9 flex h-14 w-14 items-center justify-center rounded-full bg-gray-200 text-2xl transition-all hover:bg-gray-950 hover:text-white hover:shadow-lg"
              >
                <span aria-hidden="true">&#8594;</span>
              </a>
            </div>

            <div
              class="flex items-center gap-3 text-[10px] font-semibold tracking-[0.14em] text-gray-400"
            >
              <template
                v-for="(social, index) in socialLinks"
                :key="social.href"
              >
                <span v-if="index > 0" aria-hidden="true" class="text-gray-300"
                  >/</span
                >
                <a
                  :href="social.href"
                  target="_blank"
                  rel="noreferrer"
                  class="transition-colors hover:text-gray-950"
                >
                  {{ social.label }}
                </a>
              </template>
            </div>
          </div>

          <div
            class="relative flex min-h-[22rem] items-center justify-center bg-gray-100/70 p-6 sm:p-10 md:min-h-full"
          >
            <div
              aria-hidden="true"
              class="absolute left-1/2 top-1/2 -z-0 aspect-square w-[84%] -translate-x-1/2 -translate-y-1/2 rounded-full bg-gradient-to-br from-gray-300 via-gray-100 to-white blur-xl"
            ></div>
            <img
              :src="profileImage"
              :alt="`${name} profile`"
              class="relative z-10 aspect-[3/4] w-full max-w-sm rounded-2xl object-cover grayscale"
            />
            <p
              aria-hidden="true"
              class="absolute bottom-7 right-7 z-20 [writing-mode:vertical-rl] text-[9px] font-semibold tracking-[0.28em] text-gray-400"
            >
              SCROLL DOWN
              <span class="mt-2 text-sm tracking-normal">&#8595;</span>
            </p>
          </div>
        </article>

        <p
          aria-hidden="true"
          class="pointer-events-none absolute -right-14 top-1/2 hidden -translate-y-1/2 rotate-180 [writing-mode:vertical-rl] text-7xl font-black tracking-[-0.06em] text-gray-900/[0.035] lg:block"
        >
          PORTFOLIO
        </p>
      </div>
    </div>
  </section>
</template>
