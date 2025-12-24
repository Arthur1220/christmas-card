<script setup>
import { ref, onMounted, nextTick } from 'vue' // Adicionado nextTick
import { config } from '../config.js'

const emit = defineEmits(['complete'])
const text = ref('')
const isSlidingUp = ref(false)

// Criamos uma referência direta para a caixa do terminal no HTML
const terminalRef = ref(null)

const scrollToBottom = async () => {
  // Espera o Vue atualizar o DOM (a tela)
  await nextTick()
  
  // Se a caixa existir, rola para o final
  if (terminalRef.value) {
    terminalRef.value.scrollTop = terminalRef.value.scrollHeight
  }
}

const startTyping = async () => {
  for (const line of config.mensagensTerminal) {
    for (let i = 0; i < line.length; i++) {
      text.value += line[i]
      // Velocidade de digitação
      await new Promise(r => setTimeout(r, config.velocidadeDigitacao))
      
      // FORÇA O SCROLL A CADA LETRA (Garante que o mobile acompanhe)
      await scrollToBottom()
    }
    
    text.value += '\n'
    await scrollToBottom() // Garante scroll na quebra de linha
    
    // Pausa entre linhas
    await new Promise(r => setTimeout(r, config.pausaEntreLinhas))
  }
  
  isSlidingUp.value = true
  setTimeout(() => { emit('complete') }, 800) 
}

onMounted(() => { startTyping() })
</script>

<template>
  <div class="terminal-wrapper" :class="{ 'slide-up': isSlidingUp }">
    <div class="terminal-box" ref="terminalRef">
      <pre>{{ text }}<span class="cursor">_</span></pre>
    </div>
  </div>
</template>

<style scoped>
.terminal-wrapper {
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100vh;
  background-color: var(--bg-color);
  display: flex;
  justify-content: center;
  /* IMPORTANTE: padding-top seguro para não cortar no iPhone (Notch) */
  padding-top: max(5vh, env(safe-area-inset-top)); 
  z-index: 100;
  transition: transform 1.2s cubic-bezier(0.7, 0, 0.3, 1);
}

.slide-up {
  transform: translateY(-100%);
}

.terminal-box {
  width: 90%;
  max-width: 600px;
  /* Altura fixa para permitir scroll interno */
  height: 80vh; 
  overflow-y: auto; /* Permite rolar */
  color: var(--terminal-color);
  font-size: 1rem; /* Tamanho legível */
  line-height: 1.5;
  /* Scroll suave */
  scroll-behavior: smooth; 
  /* Esconder barra de rolagem */
  scrollbar-width: none;
  padding-bottom: 50px; /* Espaço extra no final para o texto não colar na borda */
}

.terminal-box::-webkit-scrollbar { display: none; }

pre {
  white-space: pre-wrap; 
  word-wrap: break-word; 
  margin: 0;
  font-family: 'Fira Code', monospace;
}

.cursor {
  animation: blink 1s infinite;
}

@keyframes blink {
  0%, 50% { opacity: 1; }
  51%, 100% { opacity: 0; }
}
</style>