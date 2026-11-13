<script setup lang="ts">
import { ref } from 'vue'

const selectedImage = ref<string | null>(null)

const certifications = [
  {
    title: 'Introduction to Modern Database Systems',
    image: '/images/db-cert.png',
    fullImage: '/images/full-db-cert.JPG',
    verification: 'https://learn.saylor.org/admin/tool/certificate/index.php?code=6798079284JV',
  },
  {
    title: 'Software Engineering',
    image: '/images/software-cert.png',
    fullImage: '/images/full-software-cert.JPG',
    verification: 'https://learn.saylor.org/admin/tool/certificate/index.php?code=9760249764JV',
  },
  {
    title: 'Microsoft Office Specialist: Word Associate',
    image: '/images/word.png',
    fullImage: '/images/word.png',
    verification: 'https://www.credly.com/badges/5039c319-300a-4eb2-b5e8-2d722ce134c8/public_url',
  },
  {
    title: 'Microsoft Office Specialist: PowerPoint Associate',
    image: '/images/powerpoint.png',
    fullImage: '/images/powerpoint.png',
    verification: 'https://www.credly.com/badges/bd83a364-266b-499f-9375-563dc0b20625/public_url',
  },
  {
    title: 'Python Essentials 1',
    image: '/images/pe1.png',
    fullImage: '/images/pe1.png',
    verification: 'https://www.credly.com/badges/a6dd4b82-7689-4494-8e91-beb838c7c902/public_url',
  },
  {
    title: 'Networking Basics',
    image: '/images/nwbs.png',
    fullImage: '/images/nwbs.png',
    verification: 'https://www.credly.com/badges/c870902d-6a30-47f8-aaab-64ebc4b999f7/public_url',
  },
  {
    title: 'IT Specialist: Databases',
    image: '/images/databases.png',
    fullImage: '/images/databases.png',
    verification: 'https://www.credly.com/badges/a63b038e-d3d7-47d0-86c5-b13798f6bbd1/public_url',
  },
   {
    title: 'MongoDB Overview: Core Concepts and Architecture',
    image: '/images/mongodb-overview.png',
    fullImage: '/images/mongodb-overview.png',
    verification: 'https://www.credly.com/badges/dbfe2091-bcfe-4788-bd35-435999646e0f/public_url',
  },
  {
    title: 'CRUD Operations in MongoDB',
    image: '/images/mongodb-crud.png',
    fullImage: '/images/mongodb-crud.png',
    verification: 'https://www.credly.com/badges/50022ce2-eda6-4d79-b060-f8a804a2c9b9/public_url',
  },
]

useHead({
  title: 'Certifications | Jhon Philip Villegas',
})
useSeoMeta({
  description: 'Browse and verify the software, database, networking, and productivity certifications earned by Jhon Philip Villegas.',
  ogTitle: 'Certifications | Jhon Philip Villegas',
  ogDescription: 'A collection of verified technology and professional certifications earned by Jhon Philip Villegas.',
  ogType: 'website',
  twitterCard: 'summary',
})
</script>

<template>
  <main>
    <h1 class="text-center fw-bold headerss">Certifications</h1>

    <section class="cert-container">
      <CertificationCard
        v-for="certification in certifications"
        :key="certification.title"
        v-bind="certification"
        @preview="selectedImage = $event"
      />
    </section>

    <dialog
      v-if="selectedImage"
      class="modal show"
      open
      aria-label="Certificate image"
      @click.self="selectedImage = null"
      @keyup.esc.window="selectedImage = null"
    >
      <button class="close" type="button" aria-label="Close image" @click="selectedImage = null">
        &times;
      </button>
      <img class="modal-content" :src="selectedImage" alt="Enlarged certificate">
    </dialog>
  </main>
</template>
