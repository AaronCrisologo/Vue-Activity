<script setup>
import { defineProps } from 'vue'

defineProps({
  project: Object
})
</script>

<template>
  <div class="col-md-6 col-lg-4">
    <div class="card project-card h-100">
      <img :src="project.image" class="card-img-top" :alt="project.title" />
      <div class="card-body">
        <span class="project-tag" :class="`tag-${project.tag.toLowerCase().replace(/ /g, '-')}`">
          {{ project.tag }}
        </span>
        <h5 class="card-title mt-2">{{ project.title }}</h5>
        <p class="card-text">{{ project.description }}</p>
        <div class="tech-wrap">
          <span v-for="tech in project.tech" :key="tech" class="tech-badge">{{ tech }}</span>
        </div>
      </div>
    </div>
  </div>
</template>
