<script setup>
// Vue 3 Composition API: Tema gelap & jam realtime interaktif
import { ref, watch, onMounted } from 'vue'
import HelloWorld from './components/HelloWorld.vue'

// Reactive state
const isDark = ref(false)
const currentTime = ref('')

// Ubah class <body> saat tema berganti
watch(isDark, (val) => {
  document.body.className = val ? 'dark' : ''
})

// Update jam setiap detik (format lokal)
onMounted(() => {
  setInterval(() => {
    const now = new Date()
    currentTime.value = now.toLocaleTimeString()
  }, 1000)
})
</script>

<template>
  <div>
    <!-- Logo Vite -->
    <a href="https://vite.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    
    <!-- Logo Vue -->
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>

  <!-- Komponen child dengan props -->
  <HelloWorld msg="🔥 Vite + Vue powered by Composition API 🔥" />

  <!-- Jam realtime dan sambutan -->
  <p class="welcome-text">
    🎉 Selamat datang di proyek <strong>Vue + Vite</strong> interaktif!
    <br />
    🕒 Sekarang pukul: <strong>{{ currentTime }}</strong>
  </p>

  <!-- Tombol untuk toggle tema -->
  <button
    @click="isDark = !isDark"
    class="theme-toggle"
    :title="`Klik untuk ganti ke tema ${isDark ? 'Terang' : 'Gelap'}`"
  >
    {{ isDark ? '🌙 Mode Gelap Aktif' : '🌞 Mode Terang Aktif' }}
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
  font-size: 1.3rem;
  margin-top: 1rem;
  color: inherit;
  line-height: 1.8;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.theme-toggle {
  display: block;
  margin: 1.5rem auto;
  padding: 0.6rem 1.2rem;
  background-color: #42b883;
  color: white;
  border: none;
  border-radius: 12px;
  cursor: pointer;
  font-size: 1.1rem;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  transition: all 0.3s ease;
}
.theme-toggle:hover {
  background-color: #2f9774;
  transform: scale(1.05);
}
</style>

<style>
/* Global dark mode */
body.dark {
  background-color: #121212;
  color: #e0e0e0;
  transition: background-color 0.4s ease, color 0.4s ease;
}
</style>
