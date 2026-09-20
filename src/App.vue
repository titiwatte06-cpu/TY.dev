<script setup lang="ts">
import HeroSection from "./components/HeroSection.vue";
import TheFooter from "./components/TheFooter.vue";
import TheNavbar from "./components/TheNavbar.vue";
</script>

<template>
  <TheNavbar />
  <HeroSection
    name="Titiwat Yutavisut"
    description="I create thoughtful digital experiences with a focus on clarity, character, and meaningful details."
    profile-image="https://images.unsplash.com/photo-1535713875002-d1d0cf377fde?auto=format&fit=crop&w=900&q=85"
    :social-links="[
      { label: 'GITHUB', href: 'https://github.com/' },
      { label: 'LINKEDIN', href: 'https://www.linkedin.com/' },
    ]"
    :projects="[
      {
        title: 'Catholic Data',
        description:
          'เว็บแสดงตำแหน่งวัดคาทอลิกในกรุงเทพฯ พร้อมเวลามิสซาและระบบแจ้งเตือนแบบเรียลไทม์',
        techStack: ['React', 'TypeScript', 'Leaflet', 'Node.js', 'MongoDB'],
        link: 'https://catholic-data.vercel.app',
        screenshot: '/video/CatholicData.mp4',
      },
      {
        title: 'TheRealEstate',
        description:
          'เว็บสำหรับนำเสนอและค้นหาโครงการอสังหาริมทรัพย์ พร้อมข้อมูลรายละเอียดของแต่ละโครงการในรูปแบบที่ใช้งานง่าย',
        techStack: ['React', 'TypeScript', 'Tailwind CSS', 'Node.js'],
        link: '#',
        screenshot: '/video/TheRealEstate.mp4',
      },
      {
        title: 'Juicy Healthy',
        description:
          'โปรเจกต์เว็บไซต์ที่ทำร่วมกับเพื่อน ๆ ใน Bootcamp Generation Thailand เพื่อส่งเสริมการดูแลสุขภาพและการใช้ชีวิตอย่างมีคุณภาพ',
        techStack: ['React', 'JavaScript', 'CSS', 'Teamwork'],
        link: '#',
        screenshot: '/video/JuicyHealthy.mp4',
      },
      {
        title: 'Blessed Cookie',
        description:
          'เว็บขายคุกกี้ สร้างขึ้นระหว่างเรียนรู้ Next.js App Router',
        techStack: ['Next.js', 'Prisma', 'PostgreSQL', 'Express'],
        link: '#',
      },
    ]"
    :certifications="[
      {
        title: 'Certification 01',
        issuer: 'Add certificate issuer',
        image:
          'https://placehold.co/1200x900/f5f5f5/171717?text=Certificate+01',
      },
      {
        title: 'Certification 02',
        issuer: 'Add certificate issuer',
        image:
          'https://placehold.co/1200x900/e5e5e5/171717?text=Certificate+02',
      },
      {
        title: 'Certification 03',
        issuer: 'Add certificate issuer',
        image:
          'https://placehold.co/1200x900/d4d4d4/171717?text=Certificate+03',
      },
    ]"
  />
  <TheFooter />
</template>

<style scoped></style>
