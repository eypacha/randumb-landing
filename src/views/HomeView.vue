<template>
  <div class="home-view min-h-screen bg-gradient-to-br from-blue-100 to-purple-200 relative">
    <header
      class="text-center w-full py-10 px-6 md:px-16 bg-gradient-to-r from-purple-700 to-blue-500 text-white relative">
      <div class="absolute left-4 top-4 z-50">
        <select v-model="$i18n.locale" class="rounded px-2 py-1 text-sm text-white">
          <option value="es">ES</option>
          <option value="en">EN</option>
        </select>
      </div>
      <a href="https://github.com/eypacha/randumb" target="_blank">
        <img src="/forkme_right_white.png" alt="Fork me on Github" class="absolute top-0 right-0 w-50">
      </a>
      <h1 class="text-4xl font-extrabold tracking-tight">{{ $t('home.title') }}</h1>
      <h2 class="text-2xl md:text-3xl font-semibold mb-2">{{ $t('home.subtitle') }}</h2>
      <p class="text-lg md:text-xl max-w-2xl mb-4 mx-auto">{{ $t('home.description') }}</p>
      <div v-if="example"
        class="bg-white/20 text-white rounded-lg px-4 py-3 mb-4 max-w-[700px] mx-auto shadow flex flex-col items-center">
        <button @click="fetchExample" class="flex items-center gap-2 focus:outline-none group"
          :title="$t('home.exampleTooltip')">
          <span class="text-lg font-semibold italic ">{{ example }}</span>
          <span class="text-2xl select-none cursor-pointer">🎲</span>
        </button>
      </div>
      <a href="https://dev.eypacha.com/randumb/api/docs" target="_blank"
        class="inline-block bg-white text-purple-700 font-bold py-2 px-6 rounded-full shadow hover:bg-purple-100 transition">{{ $t('home.docs') }}</a>
    </header>
    <main class="w-full max-w-4xl mx-auto px-6 py-12 flex flex-col gap-12">
      <section>
        <h3 class="text-xl font-bold mb-2 text-purple-700">{{ $t('home.whatCanYouDo') }}</h3>
        <ul class="list-disc list-inside text-gray-700 space-y-1">
          <li>{{ $t('home.featurePirates') }}</li>
          <li>{{ $t('home.featureExcuses') }}</li>
          <li>{{ $t('home.featureConspiracies') }}</li>
          <li>{{ $t('home.featureSoon') }}</li>
        </ul>
      </section>
      <section>
        <h3 class="text-xl font-bold mb-2 text-purple-700">{{ $t('home.usageExample') }}</h3>
        <div class="bg-gray-900 text-green-200 rounded-lg p-4 text-sm font-mono overflow-x-auto space-y-1">
          <div>
            <span class="text-gray-400">GET</span> <a href="https://dev.eypacha.com/randumb/api/pirates/random"
              target="_blank"
              class="underline hover:text-blue-300">https://dev.eypacha.com/randumb/api/pirates/random</a>
          </div>
          <div>
            <span class="text-gray-400">GET</span> <a
              href="https://dev.eypacha.com/randumb/api/excuses/es?page=1&limit=5" target="_blank"
              class="underline hover:text-blue-300">https://dev.eypacha.com/randumb/api/excuses/es?page=1&limit=5</a>
          </div>
          <div>
            <span class="text-gray-400">GET</span> <a href="https://dev.eypacha.com/randumb/api/conspiracies/random"
              target="_blank"
              class="underline hover:text-blue-300">https://dev.eypacha.com/randumb/api/conspiracies/random</a>
          </div>
        </div>
        <p class="text-xs text-gray-500 mt-2">{{ $t('home.jsonReady') }}</p>
      </section>
      <section class="text-center">
        <p class="text-gray-700 text-lg">{{ $t('home.cta') }}</p>
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
    example.value = data.text;
  } catch (e) {
    example.value = 'Ooops... algo salió mal, volvé al rato.';
  }
}
onMounted(fetchExample);
</script>