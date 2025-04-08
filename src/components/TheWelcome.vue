<script setup lang="ts">
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'

const openReadmeInEditor = () => fetch('/__open-in-editor?file=README.md')
</script>

<template>
  <div class="dashboard">
    <div class="top-bar">
      <div id="hora">19:30</div>
      <div id="data">05/04/2025</div>

      <div class="shadow"></div>
    </div>
    <div class="main-info">
      <div class="left">
        <div class="battery-container" style="--battery-level: 40">
          <div class="battery-ring"></div>
          <div class="battery-level">97%<br /><small>Carga da bateria</small></div>
        </div>
        <div>
          <div class="label">Temperatura do Motor</div>
          <div class="value">38°C</div>
        </div>
      </div>
      <div class="center">
        <h1 id="velocidade">109</h1>
        <p>km/h</p>
      </div>
      <div class="right">
        <div>
          <div class="label">Percurso</div>
          <div class="value">188 km</div>
        </div>
        <div>
          <div class="label">Consumo Médio</div>
          <div class="value">12,3 km/l</div>
        </div>
        <div>
          <div class="label">Vel. Média</div>
          <div class="value">125 km/h</div>
        </div>
      </div>
    </div>
    <div class="bottom-bar">
      <div class="gear">P</div>
      <div class="gear">R</div>
      <div class="gear active">N</div>
      <div class="gear">D</div>
    </div>
  </div>
</template>
<style>
.battery-container {
  position: relative;
  width: 180px;
  height: 180px;
  border-radius: 50%;
  background-color: #222;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 20px auto;
}

.battery-ring {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border-radius: 50%;
  border: 10px solid cyan;
  clip-path: inset(0 round 50%);
  transform: rotate(-90deg);
  transform-origin: center;
  mask-image: conic-gradient(cyan calc(var(--battery-level, 97) * 1%), transparent 0);
  -webkit-mask-image: conic-gradient(cyan calc(var(--battery-level, 97) * 1%), transparent 0);
}

body {
  margin: 0;
  background-color: #202020;
  font-family: 'Segoe UI', sans-serif;
  color: white;
  box-sizing: border-box;
}

.dashboard {
  border: 20px solid #00f5e1;
  border-radius: 50%;
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  padding: 0rem;
  box-sizing: border-box;
  position: relative;
  overflow: hidden;
}

.dashboard::before {
  content: '';
  position: absolute;
  bottom: -600px;
  left: 0;
  right: 0;
  width: 750px;
  height: 750px;
  background-color: transparent;
  margin: auto;
  border-radius: 50%;
  border: 20px solid rgba(0, 255, 255);
}

.top-bar {
  width: 60%;
  max-width: 900px;
  height: 60px;
  background: linear-gradient(to bottom, #00f5e1, rgba(0, 0, 0, 0.5));
  border-radius: 0px 0px 50px 50px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 40px;
  font-size: 1.2rem;
  color: white;
  position: relative;
}

.shadow {
  position: absolute;
  width: 100%;
  height: 20px;
  bottom: 0;
  z-index: 1;
  left: 0;
  right: 0;
}

.top-bar .data {
  font-size: 1.2rem;
  z-index: -1;
}

.top-bar::before {
  content: '';
  position: absolute;
  top: 9px;
  left: -29px;
  width: 60px;
  height: 29px;
  z-index: 0;
  border-left: 30px solid transparent;
  border-right: 30px solid transparent;
  border-bottom: 48px solid #202020;
}

.top-bar::after {
  content: '';
  position: absolute;
  top: 9px;
  right: -29px;
  width: 60px;
  height: 29px;
  z-index: 0;
  border-left: 30px solid transparent;
  border-right: 30px solid transparent;
  border-bottom: 48px solid #202020;
}

.main-info {
  display: flex;
  justify-content: space-around;
  align-items: center;
  width: 100%;
  flex-grow: 1;
}

.left,
.right {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.center {
  text-align: center;
}

.center h1 {
  font-size: 5rem;
  color: #00fff7;
}

.center p {
  color: #00fff7;
  font-size: 1.2rem;
}

.label {
  font-size: 1.1rem;
  color: #ccc;
}

.value {
  font-size: 1.5rem;
  font-weight: bold;
}

.bottom-bar {
  display: flex;
  justify-content: center;
  gap: 1.5rem;
}

.gear {
  color: gray;
}

.gear.active {
  color: #00ff7f;
}
</style>