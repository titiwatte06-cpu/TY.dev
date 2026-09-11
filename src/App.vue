<script setup lang="ts">
import HeroSection from "./components/HeroSection.vue";
import TheNavbar from "./components/TheNavbar.vue";
</script>

<template>
  <TheNavbar />
  <HeroSection
    name="Your Name"
    role="Designer & Developer"
    description="I create thoughtful digital experiences with a focus on clarity, character, and meaningful details."
    profile-image="https://images.unsplash.com/photo-1535713875002-d1d0cf377fde?auto=format&fit=crop&w=900&q=85"
    :social-links="[
      { label: 'GITHUB', href: 'https://github.com/' },
      { label: 'LINKEDIN', href: 'https://www.linkedin.com/' },
      { label: 'DRIBBBLE', href: 'https://dribbble.com/' },
    ]"
  />
</template>

<style scoped></style>
