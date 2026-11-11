<script setup>
const tools = [
  { name: 'HTML5', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original.svg' },
  { name: 'CSS3', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/css3/css3-original.svg' },
  { name: 'Bootstrap', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/bootstrap/bootstrap-original.svg' },
  { name: 'JavaScript', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/javascript/javascript-original.svg' },
  { name: 'React', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/react/react-original.svg' },
  { name: 'Node.js', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/nodejs/nodejs-original.svg' },
  { name: 'Postman', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/postman/postman-original.svg' },
  { name: 'Git', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/git/git-original.svg' }
]
</script>

<template>
  <div id="tools" class="section-white">
    <div class="container text-center">
      <div class="mb-5">
        <span class="section-tag">My Stack</span>
        <h2 class="section-title">Core Technologies &amp; <span class="gradient-text">Tools</span></h2>
        <p class="section-sub">Technologies I use to design, build and deploy full-stack applications.</p>
      </div>
      <div class="row g-4 justify-content-center">
        <div v-for="tool in tools" :key="tool.name" class="col-6 col-md-4 col-lg-3">
          <div class="tool-item">
            <img :src="tool.icon" :alt="tool.name" :title="tool.name" />
            <span class="tool-name">{{ tool.name }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
