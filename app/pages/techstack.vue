<script setup lang="ts">
useHead({
  title: 'Tech Stack | Jhon Philip Villegas',
})
useSeoMeta({
  description: 'Explore the programming languages, web technologies, tools, and platforms used by Jhon Philip Villegas.',
  ogTitle: 'Tech Stack | Jhon Philip Villegas',
  ogDescription: 'Languages, tools, and technologies in Jhon Philip Villegas’s developer toolkit.',
  ogType: 'website',
  twitterCard: 'summary',
})

const technologies = [
  { name: 'C Language', image: '/images/c.jpg' },
  { name: 'Java', image: '/images/java.png' },
  { name: 'PostgreSQL', image: '/images/sql.png' },
  { name: 'HTML', image: '/images/html.png' },
  { name: 'CSS', image: '/images/css.png' },
  { name: 'Git', image: '/images/git.png' },
  { name: 'GitHub', image: '/images/github.png' },
  { name: 'VS Code', image: '/images/vscode.png' },
]
</script>

<template>
  <main>
    <h1 class="text-center fw-bold headerss">Tech Stack</h1>

    <div class="container a">
      <div class="tech-container">
        <TechStackCard
          v-for="technology in technologies"
          :key="technology.name"
          v-bind="technology"
        />
      </div>
    </div>
  </main>
</template>
