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
</script>

<template>
  <section
    id="home"
    class="relative isolate min-h-screen overflow-hidden bg-neutral-50 px-5 py-8 text-neutral-950 sm:px-8 lg:px-12"
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
        'absolute z-0 select-none text-xl font-light text-neutral-300',
        mark,
      ]"
      >+</span
    >

    <div
      class="mx-auto flex min-h-[calc(100vh-4rem)] max-w-6xl flex-col justify-center"
    >
      <p
        class="mb-5 text-[10px] font-medium tracking-[0.32em] text-neutral-500 sm:text-xs"
      >
        WEB DESIGN / UI / UX
        <span class="ml-2 text-neutral-400">{{ currentYear }}</span>
      </p>

      <div class="relative">
        <div
          aria-hidden="true"
          class="absolute left-1/2 top-1/2 -z-10 aspect-square w-[min(78vw,34rem)] -translate-x-1/2 -translate-y-1/2 rounded-full bg-gradient-to-br from-neutral-200 via-neutral-100 to-white blur-2xl"
        ></div>

        <article
          class="relative grid overflow-hidden rounded-3xl border border-neutral-900/15 bg-white shadow-[0_20px_70px_rgba(23,23,23,0.08)] md:grid-cols-[1.1fr_0.9fr]"
        >
          <div
            class="order-2 flex min-h-[38rem] flex-col p-6 sm:p-9 lg:p-12 md:order-1"
          >
            <div class="my-auto max-w-xl py-16 md:py-20">
              <p
                class="mb-5 text-xs font-semibold uppercase tracking-[0.26em] text-neutral-400"
              >
                {{ role }}
              </p>
              <h1
                class="max-w-lg text-5xl font-black leading-[0.96] tracking-[-0.05em] text-neutral-950 sm:text-7xl"
              >
                {{ name }}
              </h1>
              <p class="mt-7 max-w-md text-sm leading-7 text-neutral-600">
                {{ description }}
              </p>
              <a
                href="#works"
                aria-label="View works"
                class="mt-9 flex h-14 w-14 items-center justify-center rounded-full bg-neutral-200 text-2xl transition-all hover:bg-neutral-950 hover:text-white hover:shadow-lg"
              >
                <span aria-hidden="true">&#8594;</span>
              </a>
            </div>

            <div
              class="flex items-center gap-3 text-[10px] font-semibold tracking-[0.14em] text-neutral-400"
            >
              <template
                v-for="(social, index) in socialLinks"
                :key="social.href"
              >
                <span
                  v-if="index > 0"
                  aria-hidden="true"
                  class="text-neutral-300"
                  >/</span
                >
                <a
                  :href="social.href"
                  target="_blank"
                  rel="noreferrer"
                  class="transition-colors hover:text-neutral-950"
                >
                  {{ social.label }}
                </a>
              </template>
            </div>
          </div>

          <div
            class="relative order-1 flex min-h-[22rem] items-center justify-center bg-neutral-100/70 p-6 sm:p-10 md:order-2 md:min-h-full"
          >
            <div
              aria-hidden="true"
              class="absolute left-1/2 top-1/2 -z-0 aspect-square w-[84%] -translate-x-1/2 -translate-y-1/2 rounded-full bg-gradient-to-br from-neutral-300 via-neutral-100 to-white blur-xl"
            ></div>
            <img
              :src="profileImage"
              :alt="`${name} profile`"
              class="relative z-10 aspect-[3/4] w-full max-w-sm rounded-2xl object-cover grayscale"
            />
          </div>
        </article>
      </div>
    </div>
  </section>
  <section
    id="about"
    class="relative isolate overflow-hidden border-t border-neutral-200 bg-neutral-50 px-5 py-24 transition-colors duration-300 dark:border-neutral-800 dark:bg-neutral-900 sm:px-8 lg:px-12"
  >
    <div
      class="relative z-10 mx-auto grid max-w-7xl gap-12 md:grid-cols-[0.75fr_1.25fr] md:items-center md:gap-16 lg:gap-24"
    >
      <div class="flex flex-col items-center justify-center text-center">
        <p
          class="mb-6 text-xs font-bold uppercase tracking-[0.2em] text-neutral-700 dark:text-neutral-300"
        >
          Once a good learner at
        </p>
        <a
          href="https://thailand.generation.org/"
          target="_blank"
          rel="noreferrer"
          aria-label="Generation Thailand Website"
          class="inline-flex transition-opacity hover:opacity-75"
        >
          <img
            class="w-64 sm:w-80"
            src="https://res.cloudinary.com/s0vscy04/image/upload/q_auto,f_webp/v1784804807/asset-genth_rm7afy.webp"
            alt="Generation Thailand Logo"
          />
        </a>
      </div>

      <div class="max-w-2xl">
        <p
          class="text-xs font-bold uppercase tracking-[0.2em] text-neutral-500 dark:text-neutral-400"
        >
          Now, Titiwat still study harder to be a great
        </p>
        <h2
          class="mt-5 text-3xl font-black leading-[0.98] tracking-[-0.04em] text-neutral-950 dark:text-neutral-100 sm:text-6xl md:whitespace-nowrap lg:text-7xl"
        >
          Full Stack Developer
        </h2>
        <p
          class="mt-8 max-w-xl text-base leading-8 text-neutral-600 dark:text-neutral-300"
        >
          A Coding Teacher and Full Stack Developer dedicated to inspiring the
          next generation of innovators and building scalable web solutions.
          Building the web of today, shaping the innovators of tomorrow.
        </p>
        <a
          href="#projects"
          class="mt-10 inline-flex items-center border-b border-neutral-950 pb-2 text-xs font-bold uppercase tracking-[0.18em] text-neutral-950 transition-colors hover:border-neutral-500 hover:text-neutral-500 dark:border-neutral-100 dark:text-neutral-100 dark:hover:border-neutral-400 dark:hover:text-neutral-400"
        >
          Explore My Works <span class="ml-4 text-base">&#8595;</span>
        </a>
      </div>
    </div>
  </section>
</template>
