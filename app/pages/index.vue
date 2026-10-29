<script setup lang="ts">
import { onMounted, onUnmounted, ref } from 'vue'

const role = 'Aspiring Front-End Developer'
const typedRole = ref('')
let typingTimer: ReturnType<typeof setInterval> | undefined

useHead({
  title: 'Jhon Philip Villegas | Web Portfolio',
})

onMounted(() => {
  let index = 0
  typingTimer = setInterval(() => {
    typedRole.value += role.charAt(index)
    index += 1

    if (index >= role.length && typingTimer) {
      clearInterval(typingTimer)
    }
  }, 100)
})

onUnmounted(() => {
  if (typingTimer) clearInterval(typingTimer)
})
</script>

<template>
  <main class="main-container">
    <section class="home-hero">
      <div class="hero">
        <div class="hero-text">
          <img src="/images/pfp.jpg" alt="Profile Picture">
          <h2>Hi, I'm Jhon Philip Villegas</h2>
          <h3 id="typing">{{ typedRole }}</h3>
          <p>
            Welcome to my personal portfolio website. I am an aspiring front-end developer passionate about web development and designing websites.
          </p>
        </div>
      </div>
    </section>
  </main>
</template>
