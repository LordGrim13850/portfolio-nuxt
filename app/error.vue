<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps<{
  error: {
    statusCode: number
  }
}>()

const isNotFound = computed(() => props.error.statusCode === 404)
const statusCode = computed(() => props.error.statusCode || 500)
const handleReturnHome = () => clearError({ redirect: '/' })

useHead({
  title: computed(() => isNotFound.value ? 'Page Not Found | Jhon Philip Villegas' : 'Something Went Wrong | Jhon Philip Villegas'),
})
useSeoMeta({
  description: 'Portfolio page unavailable.',
  robots: 'noindex, nofollow',
})
</script>

<template>
  <div>
    <AppNavbar />
    <main class="not-found-page">
      <section class="not-found-content">
        <p class="not-found-code">{{ statusCode }}</p>
        <h1>{{ isNotFound ? 'This page is off the map.' : 'Something went wrong.' }}</h1>
        <p>
          {{ isNotFound
            ? 'The address may be outdated, or the page may have moved.'
            : 'The portfolio could not load this page right now.' }}
        </p>
        <button class="btn btn-primary" type="button" @click="handleReturnHome">
          Return to Home
        </button>
      </section>
    </main>
  </div>
</template>