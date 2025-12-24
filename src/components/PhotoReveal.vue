<script setup>
import { config } from '../config.js'
</script>

<template>
  <div class="reveal-background">
    <div class="polaroid-card">
      <div class="photo-area">
        <img :src="config.fotoFamilia" alt="Nossa Família" />
      </div>
      <div class="message-area">
        <h1>Feliz Natal!</h1>
        <p>De: {{ config.nomeAssinatura }}</p>
      </div>
    </div>
    
    <div class="snow"></div>
    <div class="snow mid"></div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&display=swap');

.reveal-background {
  width: 100vw; height: 100vh;
  background: radial-gradient(circle at center, #145213 0%, #1a0505 100%);
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  position: relative;
}

.polaroid-card {
  background: #fff;
  padding: 10px 10px 30px 10px; 
  box-shadow: 0 10px 30px rgba(0,0,0,0.5);
  transform: rotate(-3deg);
  opacity: 0;
  animation: dropIn 1.5s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
  animation-delay: 0.5s;
  
  width: 85%; 
  max-width: 380px; 
  z-index: 10;
}

.photo-area img {
  width: 100%;
  height: auto;
  display: block;
  border: 1px solid #eee;
}

.message-area {
  text-align: center;
  margin-top: 15px;
}

.message-area h1 {
  font-family: 'Dancing Script', cursive;
  font-size: 2.2rem; 
  margin: 0;
  color: #c0392b;
}

.message-area p {
  font-family: 'Fira Code', monospace;
  font-size: 0.8rem;
  color: #666;
  margin-top: 5px;
}

@keyframes dropIn {
  0% { opacity: 0; transform: translateY(-100vh) rotate(10deg); }
  100% { opacity: 1; transform: translateY(0) rotate(-3deg); }
}

.snow, .snow:before, .snow:after {
  position: absolute; top: -650px; left: 0; bottom: 0; right: 0;
  background-image: 
    radial-gradient(4px 4px at 100px 50px, #fff 50%, transparent), 
    radial-gradient(6px 6px at 200px 150px, #fff 50%, transparent), 
    radial-gradient(3px 3px at 300px 250px, #fff 50%, transparent);
  background-size: 650px 650px;
  animation: snow 10s linear infinite; opacity: 0.3; pointer-events: none;
}
.snow.mid { animation-duration: 6s; opacity: 0.2; filter: blur(2px); }
@keyframes snow { 100% { transform: translateY(650px); } }
</style>