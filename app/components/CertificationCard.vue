<script setup lang="ts">
defineProps<{
  title: string
  image: string
  fullImage: string
  verification: string
}>()

defineEmits<{
  preview: [image: string]
}>()
</script>

<template>
  <article class="cert-card card bg-base-100 shadow-xl">
    <button class="cert-image-button" type="button" :aria-label="`View ${title} certificate`" @click="$emit('preview', fullImage)">
      <img class="cert-img cert-thumb" :src="image" :alt="title">
    </button>

    <p>{{ title }}</p>

    <a
      class="verify-btn btn btn-primary"
      :href="verification"
      target="_blank"
      rel="noopener noreferrer"
    >
      Verify Credentials
    </a>
  </article>
</template>