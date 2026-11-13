<script setup lang="ts">
defineProps<{
  name: string
  image: string
}>()
</script>

<template>
  <article class="tech-card card bg-base-100 shadow-md">
    <img :src="image" :alt="name">
    <h2>{{ name }}</h2>
  </article>
</template>