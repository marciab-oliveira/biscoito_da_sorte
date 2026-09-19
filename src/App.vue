<template>
  <div class="spring-container">
    <div class="app-card">
    <MtcHeader />
    <MtcBiscoito />
    <MtcFooter />
    </div>
  </div>
</template>
<script setup>
import MtcHeader from './components/MtcHeader.vue';
import MtcBiscoito from './components/MtcBiscoito.vue';
import MtcFooter from './components/MtcFooter.vue';
</script>
<style>
body {
  margin: 0;
  padding: 0;
  font-family: 'Plus Jakarta Sans', sans-serif;
  -webkit-font-smoothing: antialiased;
  background: linear-gradient(135deg, #1e2229 0%, #11141a 100%);
}
.spring-container {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  padding: 16px;
  box-sizing: border-box;
  background: rgba(30, 34, 42, 0.4); /* Camada cinza bem transparente */
  backdrop-filter: blur(12px); /* Borra o fundo de forma super premium */
  -webkit-backdrop-filter: blur(12px); /* Garante o funcionamento perfeito em iPhones/iOS */
}
.app-card {
  background-image: url('/public/fundo-primavera.png');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  border-radius: 28px; /* Cantos bem arredondados como telas modernas de celular */
  width: 100%;
  max-width: 410px;
  padding: 28px 24px;
  min-height: 85vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  /* Uma borda branca finíssima imitando o reflexo da luz na quina do vidro */
  border: 1px solid rgba(255, 255, 255, 0.25);
  /* Sombra pro card parecer que está flutuando fisicamente em cima do fundo chumbo */
  box-shadow: 0 24px 60px rgba(0, 0, 0, 0.45);
  position: relative;
  overflow: hidden;
}
</style>
