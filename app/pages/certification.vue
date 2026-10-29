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
]

useHead({
  title: 'Certifications | Jhon Philip Villegas',
})
</script>

<template>
  <main>
    <h1 class="text-center fw-bold headerss">Certifications</h1>

    <section class="cert-container">
      <article v-for="certification in certifications" :key="certification.title" class="cert-card">
        <img
          class="cert-img cert-thumb"
          :src="certification.image"
          :alt="certification.title"
          role="button"
          tabindex="0"
          @click="selectedImage = certification.fullImage"
          @keydown.enter="selectedImage = certification.fullImage"
          @keydown.space.prevent="selectedImage = certification.fullImage"
        >

        <p>{{ certification.title }}</p>

        <a
          class="verify-btn btn btn-primary"
          :href="certification.verification"
          target="_blank"
          rel="noopener noreferrer"
        >
          Verify Credentials
        </a>
      </article>
    </section>

    <div
      v-if="selectedImage"
      class="modal show"
      role="dialog"
      aria-modal="true"
      aria-label="Certificate image"
      @click.self="selectedImage = null"
      @keyup.esc.window="selectedImage = null"
    >
      <button class="close" type="button" aria-label="Close image" @click="selectedImage = null">
        &times;
      </button>
      <img class="modal-content" :src="selectedImage" alt="Enlarged certificate">
    </div>
  </main>
</template>
