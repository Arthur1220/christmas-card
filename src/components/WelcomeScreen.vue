<script setup>
const emit = defineEmits(['start'])
</script>

<template>
  <div class="welcome-container">
    <h1>🎄 System Ready</h1>
    <p>Uma mensagem criptografada aguarda...</p>
    
    <p class="hint">( 🔊 Aumente o som para a melhor experiência )</p>
    
    <button @click="$emit('start')">
      INICIAR PROTOCOLO >_
    </button>
  </div>
</template>

<style scoped>
.welcome-container {
  text-align: center;
  z-index: 10;
  padding: 20px; 
  width: 100%;
  box-sizing: border-box;
}

h1 {
  font-size: 2rem;
  margin-bottom: 10px;
}

p {
  font-size: 1rem;
  margin-bottom: 5px;
}

.hint {
  font-size: 0.85rem;
  opacity: 0.8;
  margin-bottom: 30px;
  color: #aaffaa; 
  animation: pulse 2s infinite;
}

button {
  background: transparent;
  border: 2px solid var(--terminal-color);
  color: var(--terminal-color);
  padding: 15px 25px; 
  font-size: 1.1rem;
  cursor: pointer;
  transition: 0.3s;
  width: 100%; 
  max-width: 300px;
  border-radius: 8px; 
}

button:active {
  background: var(--terminal-color);
  color: var(--bg-color);
}

@keyframes pulse {
  0%, 100% { opacity: 0.6; }
  50% { opacity: 1; }
}
</style>