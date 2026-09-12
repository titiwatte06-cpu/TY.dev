<script setup lang="ts">
import ProjectCard from "./ProjectCard.vue";
import ProjectCardSkeleton from "./ProjectCardSkeleton.vue";
import { computed, ref } from "vue";

interface SocialLink {
  label: string;
  href: string;
}

interface Project {
  title: string;
  description: string;
  techStack: string[];
  link: string;
  screenshot?: string;
}

interface Certification {
  title: string;
  issuer: string;
  image: string;
}

interface Props {
  name: string;
  role: string;
  description: string;
  profileImage: string;
  socialLinks: SocialLink[];
  projects: Project[];
  certifications: Certification[];
}

const { certifications } = defineProps<Props>();

const isLoadingProjects = ref(false);
const certificationIndex = ref(0);
const currentCertification = computed<Certification>(
  () =>
    certifications[certificationIndex.value] ?? {
      title: "",
      issuer: "",
      image: "",
    },
);

function showPreviousCertification() {
  if (certifications.length === 0) return;
  certificationIndex.value =
    (certificationIndex.value - 1 + certifications.length) %
    certifications.length;
}

function showNextCertification() {
  if (certifications.length === 0) return;
  certificationIndex.value =
    (certificationIndex.value + 1) % certifications.length;
}

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
    <div class="relative z-10 mx-auto max-w-7xl">
      <div class="mx-auto max-w-4xl text-center">
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
          class="mx-auto mt-8 max-w-xl text-center text-base leading-8 text-neutral-600 dark:text-neutral-300"
        >
          A Coding Teacher and Full Stack Developer dedicated to inspiring the
          next generation of innovators and building scalable web solutions.
          Building the web of today, shaping the innovators of tomorrow.
        </p>
      </div>

      <div
        class="mt-20 grid gap-16 border-t border-neutral-200 pt-12 dark:border-neutral-800 md:grid-cols-2 md:gap-0"
      >
        <article
          class="flex flex-col items-center text-center md:border-r md:border-neutral-200 md:pr-12 dark:md:border-neutral-800"
        >
          <p
            class="text-xs font-bold uppercase tracking-[0.2em] text-neutral-700 dark:text-neutral-300"
          >
            Education
          </p>
          <a
            href="https://www.ru.ac.th/"
            target="_blank"
            rel="noreferrer"
            aria-label="Ramkhamhaeng University Website"
            class="mt-8 transition-opacity hover:opacity-75"
          >
            <img
              class="h-40 w-40 object-contain dark:invert"
              src="https://commons.wikimedia.org/wiki/Special:FilePath/Emblem%20of%20Ramkhamhaeng%20University%2C%20BW.svg"
              alt="Ramkhamhaeng University Emblem"
            />
          </a>
          <h3
            class="mt-8 text-2xl font-black leading-tight text-neutral-950 dark:text-neutral-100 sm:text-3xl"
          >
            Ramkhamhaeng University
          </h3>
          <p
            class="mt-3 text-sm font-semibold uppercase tracking-[0.14em] text-neutral-500 dark:text-neutral-400"
          >
            Computer Science · Started in 2025
          </p>
        </article>

        <article class="flex flex-col items-center text-center md:pl-12">
          <p
            class="text-xs font-bold uppercase tracking-[0.2em] text-neutral-700 dark:text-neutral-300"
          >
            Bootcamp Experience
          </p>
          <a
            href="https://thailand.generation.org/"
            target="_blank"
            rel="noreferrer"
            aria-label="Generation Thailand Website"
            class="mt-8 inline-flex transition-opacity hover:opacity-75"
          >
            <img
              class="h-40 w-64 object-contain sm:w-80"
              src="https://res.cloudinary.com/s0vscy04/image/upload/q_auto,f_webp/v1784804807/asset-genth_rm7afy.webp"
              alt="Generation Thailand Logo"
            />
          </a>
          <h3
            class="mt-8 text-2xl font-black leading-tight text-neutral-950 dark:text-neutral-100 sm:text-3xl"
          >
            Generation Thailand
          </h3>
          <p
            class="mt-3 max-w-md text-sm leading-7 text-neutral-600 dark:text-neutral-300"
          >
            Completed a coding bootcamp focused on building practical skills for
            a career in software development.
          </p>
        </article>
      </div>
    </div>
  </section>
  <section
    id="projects"
    class="relative isolate overflow-hidden border-t border-neutral-200 bg-white px-5 py-24 transition-colors duration-300 dark:border-neutral-800 dark:bg-neutral-950 sm:px-8 lg:px-12"
  >
    <div class="mx-auto max-w-7xl">
      <div class="mb-16 max-w-2xl">
        <p
          class="text-xs font-bold uppercase tracking-[0.2em] text-neutral-500 dark:text-neutral-400"
        >
          Continuous learning journey
        </p>
        <h2
          class="mt-5 text-3xl font-black leading-[0.98] tracking-[-0.04em] text-neutral-950 dark:text-neutral-100 sm:text-6xl"
        >
          Featured Projects
        </h2>
      </div>

      <div class="flex flex-col gap-16">
        <template v-if="isLoadingProjects">
          <ProjectCardSkeleton
            v-for="i in 2"
            :key="i"
            :reversed="i % 2 === 0"
          />
        </template>
        <template v-else>
          <ProjectCard
            v-for="(project, i) in projects"
            :key="project.title"
            v-bind="project"
            :reversed="i % 2 === 1"
          />
        </template>
      </div>
    </div>
  </section>
  <section
    id="certificates"
    class="border-t border-neutral-200 bg-neutral-50 px-5 py-24 text-neutral-950 dark:border-neutral-800 dark:bg-neutral-900 dark:text-neutral-100 sm:px-8 lg:px-12"
  >
    <div class="mx-auto max-w-7xl">
      <div
        class="flex flex-col justify-between gap-8 border-b border-neutral-200 pb-10 dark:border-neutral-800 sm:flex-row sm:items-end"
      >
        <div>
          <p
            class="text-xs font-bold uppercase tracking-[0.22em] text-neutral-500 dark:text-neutral-400"
          >
            Credentials / 03
          </p>
          <h2
            class="mt-5 max-w-xl text-4xl font-black leading-[0.95] tracking-[-0.04em] sm:text-6xl"
          >
            Certifications
          </h2>
        </div>
        <div class="flex items-baseline gap-3">
          <span class="text-6xl font-black leading-none tracking-[-0.06em]">{{
            certifications.length
          }}</span>
          <span
            class="text-xs font-bold uppercase tracking-[0.18em] text-neutral-500 dark:text-neutral-400"
            >earned</span
          >
        </div>
      </div>

      <div v-if="certifications.length" class="mt-12">
        <div
          class="mx-auto flex max-w-5xl items-center justify-center gap-4 sm:gap-8"
        >
          <button
            type="button"
            aria-label="Previous certification"
            class="flex h-11 w-11 shrink-0 items-center justify-center rounded-full border border-neutral-300 text-xl text-neutral-700 transition-colors hover:bg-neutral-950 hover:text-white dark:border-neutral-700 dark:text-neutral-300 dark:hover:bg-neutral-100 dark:hover:text-neutral-950"
            @click="showPreviousCertification"
          >
            <span aria-hidden="true">&#8592;</span>
          </button>

          <article class="w-full max-w-3xl text-center">
            <div
              class="overflow-hidden border border-neutral-200 bg-white shadow-[0_12px_35px_rgba(23,23,23,0.06)] dark:border-neutral-800 dark:bg-neutral-950"
            >
              <img
                :key="currentCertification.image"
                :src="currentCertification.image"
                :alt="`${currentCertification.title} certificate`"
                class="aspect-[4/3] w-full object-cover grayscale transition duration-500 hover:grayscale-0"
              />
            </div>
            <h3 class="mt-5 text-base font-bold">
              {{ currentCertification.title }}
            </h3>
            <p class="mt-1 text-sm text-neutral-500 dark:text-neutral-400">
              {{ currentCertification.issuer }}
            </p>
            <p
              class="mt-4 text-[10px] font-bold uppercase tracking-[0.18em] text-neutral-400"
            >
              {{ certificationIndex + 1 }} / {{ certifications.length }}
            </p>
          </article>

          <button
            type="button"
            aria-label="Next certification"
            class="flex h-11 w-11 shrink-0 items-center justify-center rounded-full border border-neutral-300 text-xl text-neutral-700 transition-colors hover:bg-neutral-950 hover:text-white dark:border-neutral-700 dark:text-neutral-300 dark:hover:bg-neutral-100 dark:hover:text-neutral-950"
            @click="showNextCertification"
          >
            <span aria-hidden="true">&#8594;</span>
          </button>
        </div>
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
