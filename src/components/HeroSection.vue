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

function socialIcon(label: string) {
  const icons: Record<string, string> = {
    github:
      "https://api.iconify.design/simple-icons/github.svg?color=%23181717",
    linkedin:
      "https://api.iconify.design/simple-icons/linkedin.svg?color=%230A66C2",
  };

  return (
    icons[label.toLowerCase()] ??
    "https://api.iconify.design/simple-icons/link.svg?color=%23525252"
  );
}
</script>

<template>
  <section
    id="home"
    class="relative isolate min-h-screen overflow-hidden bg-white text-neutral-950"
  >
    <article
      class="grid min-h-screen overflow-hidden md:grid-cols-[1.1fr_0.9fr]"
    >
      <div
        class="order-2 flex min-h-[50vh] flex-col justify-center p-8 sm:p-12 lg:p-20 md:order-1 md:min-h-screen"
      >
        <div class="max-w-xl">
          <p
            class="hero-copy hero-delay-1 mb-5 text-xs font-semibold uppercase tracking-[0.26em] text-neutral-400"
          >
            {{ role }}
          </p>
          <h1
            class="hero-copy hero-delay-2 max-w-lg text-5xl font-black leading-[0.96] tracking-[-0.05em] text-neutral-950 sm:text-7xl"
          >
            {{ name }}
          </h1>
          <p
            class="hero-copy hero-delay-3 mt-7 max-w-md text-sm leading-7 text-neutral-600"
          >
            {{ description }}
          </p>
        </div>

        <div class="hero-copy hero-delay-4 mt-14 flex items-center gap-5">
          <template v-for="social in socialLinks" :key="social.href">
            <a
              :href="social.href"
              target="_blank"
              rel="noreferrer"
              :aria-label="social.label"
              :title="social.label"
              class="rounded-md p-1 transition-transform hover:scale-110"
            >
              <img
                :src="socialIcon(social.label)"
                :alt="`${social.label} logo`"
                class="h-7 w-7"
              />
            </a>
          </template>
        </div>

        <a
          href="/cv.pdf"
          download
          aria-label="Download CV"
          class="hero-copy hero-delay-5 mt-7 inline-flex w-fit whitespace-nowrap rounded-md border border-neutral-950 px-3 py-2 text-xs font-bold uppercase tracking-[0.12em] text-neutral-950 transition-colors hover:bg-neutral-950 hover:text-white"
        >
          Download CV
        </a>
      </div>

      <div
        class="relative order-1 flex min-h-[50vh] items-center justify-center bg-neutral-100 p-4 sm:p-8 md:order-2 md:min-h-screen"
      >
        <img
          :src="profileImage"
          :alt="`${name} profile`"
          class="hero-image relative z-10 aspect-[3/4] w-full max-w-lg rounded-2xl object-cover grayscale"
        />
      </div>
    </article>
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

<style scoped>
@keyframes hero-rise {
  from {
    opacity: 0;
    transform: translateY(16px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes hero-image-in {
  from {
    opacity: 0;
    transform: scale(0.97);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

.hero-copy {
  animation: hero-rise 700ms cubic-bezier(0.22, 1, 0.36, 1) both;
}

.hero-delay-1 {
  animation-delay: 80ms;
}

.hero-delay-2 {
  animation-delay: 160ms;
}

.hero-delay-3 {
  animation-delay: 240ms;
}

.hero-delay-4 {
  animation-delay: 320ms;
}

.hero-delay-5 {
  animation-delay: 400ms;
}

.hero-image {
  animation: hero-image-in 900ms cubic-bezier(0.22, 1, 0.36, 1) 120ms both;
}

@media (prefers-reduced-motion: reduce) {
  .hero-copy,
  .hero-image {
    animation: none;
  }
}
</style>
