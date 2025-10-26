<template>
  <div class="home-view min-h-screen bg-gradient-to-br from-blue-100 to-purple-200">
    <header class="text-center w-full py-10 px-6 md:px-16 bg-gradient-to-r from-purple-700 to-blue-500 text-white">

      <h1 class="text-4xl font-extrabold tracking-tight">Randumb API</h1>
      <h2 class="text-2xl md:text-3xl font-semibold mb-2">¡Agrega diversión instantánea a tu app!</h2>
      <p class="text-lg md:text-xl max-w-2xl mb-4 mx-auto">Insultos piratas y excusas aleatorias para bots, juegos,
        chats y más.
        Simple, rápido y sin registro.</p>
      <div v-if="example"
        class="bg-white/20 text-white rounded-lg px-4 py-3 mb-4 max-w-[700px] mx-auto shadow flex flex-col items-center">
        <button @click="fetchExample" class="flex items-center gap-2 focus:outline-none group" title="Clic para ver otro ejemplo">
          <span class="text-lg font-semibold italic ">{{ example }}</span>
          <span class="text-2xl select-none cursor-pointer">🎲</span>
        </button>
      </div>
      <div>

      </div>
      <a href="https://dev.eypacha.com/randumb/api/docs" target="_blank"
        class="inline-block bg-white text-purple-700 font-bold py-2 px-6 rounded-full shadow hover:bg-purple-100 transition">Ver
        documentación</a>
    </header>
    <main class="w-full max-w-4xl mx-auto px-6 py-12 flex flex-col gap-12">
      <section>
        <h3 class="text-xl font-bold mb-2 text-purple-700">¿Qué puedes hacer?</h3>
        <ul class="list-disc list-inside text-gray-700 space-y-1">
          <li>Genera insultos piratas para tus juegos o bots</li>
          <li>Obtén excusas para llegar tarde</li>
          <li>Obtén conspiraciones aleatorias para evangelizar a los demás</li>
        </ul>
      </section>
      <section>
        <h3 class="text-xl font-bold mb-2 text-purple-700">Ejemplo de uso</h3>
        <div class="bg-gray-900 text-green-200 rounded-lg p-4 text-sm font-mono overflow-x-auto space-y-1">
          <div>
            <span class="text-gray-400">GET</span> <a href="https://dev.eypacha.com/randumb/api/pirates/random"
              target="_blank" class="underline hover:text-blue-300">https://dev.eypacha.com/randumb/api/pirates/random</a>
          </div>
          <div>
            <span class="text-gray-400">GET</span> <a href="https://dev.eypacha.com/randumb/api/excuses/es?page=1&limit=5"
              target="_blank"
              class="underline hover:text-blue-300">https://dev.eypacha.com/randumb/api/excuses/es?page=1&limit=5</a>
          </div>
          <div>
            <span class="text-gray-400">GET</span> <a href="https://dev.eypacha.com/randumb/api/conspiracies/random"
              target="_blank" class="underline hover:text-blue-300">https://dev.eypacha.com/randumb/api/conspiracies/random</a>
          </div>
        </div>
        <p class="text-xs text-gray-500 mt-2">Recibe respuestas en JSON listas para usar.</p>
      </section>
      <section class="text-center">
        <p class="text-gray-700 text-lg">¡Empieza a usar Randumb API y sorprende a tus usuarios con contenido
          inesperado!</p>
      </section>
    </main>
    <footer class="w-full text-center text-gray-400 text-xs py-6">
      &copy; 2025 Randumb API
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const example = ref('');
async function fetchExample() {
  try {
    const res = await fetch('https://dev.eypacha.com/randumb/api/pirates/random');
    const data = await res.json();
    example.value = data.text || data.insulto || data.excuse || JSON.stringify(data);
  } catch (e) {
    example.value = 'No se pudo obtener un ejemplo.';
  }
}
onMounted(fetchExample);
</script>