<template>
  <div class="game-stage" :class="estadoBiscoito" @click="interagirBiscoito">
    <!-- As duas metades do biscoito da sorte -->
    <div class="cookie-half left">🥠</div>
    <div class="cookie-half right">🥠</div>
    <div class="papiro">
      <div class="papiro-content">
        <p v-if="conselhoAtual" class="fortune-text">{{ conselhoAtual }}</p>
      </div>
    </div>
  </div>
  <button @click="interagirBiscoito" class="spring-btn" :disabled="estadoBiscoito === 'abrindo'">
    {{ botaoTexto }}
  </button>
</template>
<script setup>
import { ref, computed } from 'vue';
import { conselhosMTC } from '../data/appData.js';
const estadoBiscoito = ref('fechado');
const conselhoAtual = ref('');
const botaoTexto = computed(() => {
  if (estadoBiscoito.value === 'aberto') return 'Pegar outro Biscoito';
  if (estadoBiscoito.value === 'abrindo') return 'Abrindo...';
  return 'Abrir Biscoito';
});
const interagirBiscoito = () => {
  if (estadoBiscoito.value === 'aberto') {
    estadoBiscoito.value = 'fechado';
    conselhoAtual.value = '';
    return;
  }
  if (estadoBiscoito.value === 'abrindo') return;
  estadoBiscoito.value = 'abrindo';
  const indiceAleatorio = Math.floor(Math.random() * conselhosMTC.length);
  conselhoAtual.value = conselhosMTC[indiceAleatorio];
  setTimeout(() => {
    estadoBiscoito.value = 'aberto';
  }, 600);
};
</script>
<style scoped>
.game-stage {
  position: relative;
  width: 300px;
  height: 200px;
  margin: 20px 0;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}
.cookie-half {
  font-size: 6rem;
  position: absolute;
  transition: transform 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  user-select: none;
  z-index: 2;
}
.cookie-half.left {
  clip-path: inset(0 50% 0 0);
  transform: translateX(0);
}
.cookie-half.right {
  clip-path: inset(0 0 0 50%);
  transform: translateX(0);
}
.abrindo .cookie-half.left,
.aberto .cookie-half.left {
  transform: translateX(-130px) rotate(-20deg) scale(0.75);
}
.abrindo .cookie-half.right,
.aberto .cookie-half.right {
  transform: translateX(130px) rotate(20deg) scale(0.75);
}
.papiro {
  position: absolute;
  width: 0;
  height: 90px;
  background: #fdf6e2;
  border-top: 2px solid #8b5a2b;
  border-bottom: 2px solid #8b5a2b;
  box-shadow: 0 4px 10px rgba(0,0,0,0.08);
  z-index: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  transition: width 0.6s ease-in-out, padding 0.6s ease-in-out;
  transition-delay: 0.2s;
}
.aberto .papiro {
  width: 250px;
  padding: 5px 15px;
}
.papiro-content {
  width: 220px;
}
.fortune-text {
  font-size: 0.85rem;
  font-weight: 500;
  color: #3e2723;
  margin: 0;
  line-height: 1.3;
  font-style: italic;
  font-family: 'Georgia', serif;
  text-align: center;
}
.spring-btn {
  background: rgba(255, 255, 255, 0.4); 
  backdrop-filter: blur(4px);
  -webkit-backdrop-filter: blur(4px);
  border: 2px solid rgba(163, 120, 83, 0.35); 
  color: #08570d; 
  padding: 12px 28px; 
  font-size: 0.92rem;
  font-weight: 500; 
  border-radius: 50px; 
  cursor: pointer;
  box-shadow: 0 4px 15px rgba(163, 120, 83, 0.05);
  transition: all 0.4s cubic-bezier(0.25, 1, 0.5, 1);
  width: auto; 
  min-width: 200px;
  letter-spacing: 0.02em;
}
/* Interatividade: Efeito Desabrochar ao tocar/passar o dedo */
.spring-btn:hover:not(:disabled) {
  transform: translateY(-2px) scale(1.02); 
  background: rgba(250, 232, 235, 0.8); 
  border-color: rgba(235, 150, 165, 0.5); 
  color: #163a18;
  box-shadow: 0 8px 20px rgba(235, 150, 165, 0.2);
}
/* Efeito físico de clique */
.spring-btn:active:not(:disabled) {
  transform: translateY(1px) scale(0.98);
}
/* Estado desabilitado quando o biscoito abre */
.spring-btn:disabled {
  background: rgba(255, 255, 255, 0.2);
  color: #a39388;
  border-color: rgba(163, 120, 83, 0.15);
  box-shadow: none;
  cursor: not-allowed;
}
@media (max-width: 480px) {
  .game-stage {
    width: 100%;
    max-width: 300px;
    height: 160px;
    margin: 15px 0;
  }
  .cookie-half {
    font-size: 4.5rem;
  }
  .abrindo .cookie-half.left,
  .aberto .cookie-half.left {
    transform: translateX(-110px) rotate(-20deg) scale(0.55);
  }
  .abrindo .cookie-half.right,
  .aberto .cookie-half.right {
    transform: translateX(110px) rotate(20deg) scale(0.55);
  }
  .aberto .papiro {
    width: 180px;
    padding: 8px 12px;
    height: 110px; 
  }
  .papiro-content {
    width: 100%;
  }
  .fortune-text {
    font-size: 0.8rem;
    line-height: 1.3;
  }
  .spring-btn {
    padding: 12px 24px;
    font-size: 0.88rem;
    min-width: 180px;
  }
}
</style>
