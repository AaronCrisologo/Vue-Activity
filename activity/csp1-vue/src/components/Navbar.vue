<script setup>
import { onMounted, onUnmounted, ref } from 'vue'

const logoVisible = ref(false)

const toggleLogo = () => {
  const nav = document.querySelector('.navbar')
  const landing = document.getElementById('landing')
  if (!nav || !landing) return
  const pastLanding = window.scrollY > (landing.offsetTop + landing.offsetHeight - 80)
  logoVisible.value = pastLanding
}

onMounted(() => {
  window.addEventListener('scroll', toggleLogo, { passive: true })
  toggleLogo()
})

onUnmounted(() => {
  window.removeEventListener('scroll', toggleLogo)
})
</script>

<template>
  <nav
    class="navbar navbar-expand-md navbar-light bg-white sticky-top shadow-sm"
    :class="{ 'logo-visible': logoVisible }"
  >
    <div class="container">
      <a class="navbar-brand fw-bold brand-logo" href="#landing">
        <img src="/images/1x1 photo.jpg" alt="Aaron Crisologo logo" class="brand-logo-img" /> AARON CRISOLOGO
      </a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ms-auto align-items-md-center">
          <li class="nav-item">
            <a class="nav-link active" href="#landing">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#projects">Projects</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#tools">Tools</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#contact">Contacts</a>
          </li>
          <li class="nav-item ms-md-3">
            <a href="#contact" class="btn btn-hire px-4">Hire Me</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
