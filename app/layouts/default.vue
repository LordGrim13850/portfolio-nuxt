<script setup lang="ts">
import { ref } from 'vue'

const menuOpen = ref(false)
</script>

<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-dark navbar-custom">
      <div class="container">
        <NuxtLink class="navbar-brand fw-bold" to="/" @click="menuOpen = false">
          JPV
        </NuxtLink>

        <button
          class="navbar-toggler"
          type="button"
          :aria-expanded="menuOpen"
          aria-controls="navbarNav"
          aria-label="Toggle navigation"
          @click="menuOpen = !menuOpen"
        >
          <span class="navbar-toggler-icon" />
        </button>

        <div id="navbarNav" class="collapse navbar-collapse" :class="{ show: menuOpen }">
          <ul class="navbar-nav ms-auto text-center">
            <li class="nav-item">
              <NuxtLink class="nav-link" exact-active-class="active" to="/" @click="menuOpen = false">
                Home
              </NuxtLink>
            </li>
            <li class="nav-item">
              <NuxtLink class="nav-link" active-class="active" to="/about" @click="menuOpen = false">
                About Me
              </NuxtLink>
            </li>
            <li class="nav-item">
              <NuxtLink class="nav-link" active-class="active" to="/techstack" @click="menuOpen = false">
                Tech Stack
              </NuxtLink>
            </li>
            <li class="nav-item">
              <NuxtLink class="nav-link" active-class="active" to="/certification" @click="menuOpen = false">
                Certifications
              </NuxtLink>
            </li>
          </ul>
        </div>
      </div>
    </nav>

    <slot />
  </div>
</template>
