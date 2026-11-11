<script setup>
import { computed } from 'vue'
import ProjectCard from './ProjectCard.vue'
import projects from '../data/projects.json'

const chunkSize = 3

const chunkedProjects = computed(() => {
  const chunks = []
  for (let i = 0; i < projects.length; i += chunkSize) {
    chunks.push(projects.slice(i, i + chunkSize))
  }
  return chunks
})
</script>

<template>
  <section class="pb-5" id="projects">
    <div class="container">
      <div class="text-center mb-5">
        <span class="section-tag">Portfolio</span>
        <h2 class="section-title">Featured Projects</h2>
        <p class="section-sub">
          A selection of my API documentation, applications, and UI mockups / prototypes.
        </p>
      </div>
      <div
        v-for="(group, index) in chunkedProjects"
        :key="index"
        class="row g-4 my-5 justify-content-center align-items-stretch"
      >
        <ProjectCard
          v-for="project in group"
          :key="project.id"
          :project="project"
        />
      </div>
    </div>
  </section>
</template>
