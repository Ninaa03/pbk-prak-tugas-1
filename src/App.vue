<script setup>
import { ref, watch } from 'vue'
import HelloWorld from './components/HelloWorld.vue'

const isDark = ref(false)

watch(isDark, (val) => {
  document.body.className = val ? 'dark' : ''
})
</script>

<template>
  <div>
    <a href="https://vite.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>

  <HelloWorld msg="Vite + Vue" />
  <p class="welcome-text">Selamat datang di proyek Vue + Vite!</p>
  <button @click="isDark = !isDark" class="theme-toggle">
    Ganti ke {{ isDark ? 'Terang' : 'Gelap' }}
  </button>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

.welcome-text {
  text-align: center;
  font-size: 1.2rem;
  margin-top: 1rem;
  color: inherit;
}

.theme-toggle {
  display: block;
  margin: 1rem auto;
  padding: 0.5rem 1rem;
  background-color: #646cff;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}
.theme-toggle:hover {
  background-color: #4b56cc;
}
</style>

<style>
/* Style global (tidak scoped) */
body.dark {
  background-color: #121212;
  color: #e0e0e0;
}
</style>
