<script setup lang="ts">
import { ref, computed, onUnmounted } from 'vue'

// Estado do cronômetro
const timer = ref(0)
const isRunning = ref(false)
let interval: number | null = null

// Estado do temporizador
const countdownTime = ref(0)
const isCountdownRunning = ref(false)

// Formatação do tempo
const formattedTime = computed(() => {
  const minutes = Math.floor(timer.value / 60)
  const seconds = timer.value % 60
  return `${String(minutes).padStart(2, '0')}:${String(seconds).padStart(2, '0')}`
})

// Funções do cronômetro
const startTimer = () => {
  isRunning.value = true
  interval = setInterval(() => {
    timer.value++
  }, 1000)
}

const stopTimer = () => {
  isRunning.value = false
  if (interval) {
    clearInterval(interval)
    interval = null
  }
}

const resetTimer = () => {
  stopTimer()
  timer.value = 0
}

// Funções do temporizador
const startCountdown = () => {
  if (countdownTime.value <= 0) return
  
  isCountdownRunning.value = true
  timer.value = countdownTime.value
  interval = setInterval(() => {
    if (timer.value > 0) {
      timer.value--
    } else {
      stopTimer()
      alert('Tempo esgotado!')
    }
  }, 1000)
}

// Limpeza ao desmontar
onUnmounted(() => {
  if (interval) {
    clearInterval(interval)
  }
})
</script>

<template>
  <div class="flex flex-col items-center justify-center min-h-screen bg-gray-50">
    <h1 class="text-4xl font-bold mb-8">Tique-Taque</h1>
    
    <!-- Display do tempo -->
    <div class="text-8xl font-mono mb-8">
      {{ formattedTime }}
    </div>

    <!-- Controles do cronômetro -->
    <div class="flex gap-4 mb-8">
      <button 
        @click="startTimer"
        class="px-6 py-2 bg-green-500 text-white rounded hover:bg-green-600"
        :disabled="isRunning"
      >
        Iniciar
      </button>
      <button 
        @click="stopTimer"
        class="px-6 py-2 bg-red-500 text-white rounded hover:bg-red-600"
        :disabled="!isRunning"
      >
        Parar
      </button>
      <button 
        @click="resetTimer"
        class="px-6 py-2 bg-blue-500 text-white rounded hover:bg-blue-600"
      >
        Zerar
      </button>
    </div>

    <!-- Controles do temporizador -->
    <div class="flex flex-col items-center gap-4">
      <div class="flex gap-2">
        <input
          v-model.number="countdownTime"
          type="number"
          min="0"
          placeholder="Segundos"
          class="px-4 py-2 border rounded"
          :disabled="isCountdownRunning"
        >
      </div>
      <button
        @click="startCountdown"
        class="px-6 py-2 bg-purple-500 text-white rounded hover:bg-purple-600"
        :disabled="isCountdownRunning"
      >
        Iniciar Temporizador
      </button>
    </div>
  </div>
</template>
