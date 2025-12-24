<script setup>
import { ref } from 'vue'
import WelcomeScreen from './components/WelcomeScreen.vue'
import TerminalOutput from './components/TerminalOutput.vue'
import PhotoReveal from './components/PhotoReveal.vue'
import { config } from './config.js'

const currentStep = ref('welcome')
const audioPlayer = ref(null)

const handleStart = () => {
  if (audioPlayer.value) {
    audioPlayer.value.volume = 0.3
    audioPlayer.value.play().catch(e => console.log("Erro áudio:", e))
  }
  currentStep.value = 'terminal'
}

const handleTerminalComplete = () => {
  currentStep.value = 'reveal'
}
</script>

<template>
  <main>
    <audio ref="audioPlayer" loop :src="config.musicaFundo"></audio>

    <WelcomeScreen 
      v-if="currentStep === 'welcome'" 
      @start="handleStart" 
    />

    <TerminalOutput 
      v-if="currentStep === 'terminal'" 
      @complete="handleTerminalComplete" 
    />

    <PhotoReveal 
      v-if="currentStep === 'reveal'" 
    />
  </main>
</template>