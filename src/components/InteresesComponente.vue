<script setup>
import { ref } from 'vue'
import FondoAnimado from './FondoAnimado.vue' // se usa tu componente real

// Lista reactiva de intereses
const intereses = ref([
  'Desarrollo de Videojuegos: me encanta crear experiencias interactivas y aprender sobre motores como Unity o Unreal, combinando programación, diseño y narrativa.',
  'Entrenamiento en Gimnasio: disfruto entrenar con constancia, siempre buscando mejorar mi rendimiento y mantener una buena salud física y mental.',
  'Fútbol: Me gusta mucho el fútbol, tanto para verlo como para jugarlo.',
  'Piano: toco el piano como forma de desconexión y creatividad, explorando distintos estilos musicales y mejorando mi técnica día a día.'
])
</script>
<template>
  <div class="intereses-contenedor">
    <!-- 🌌 Fondo animado -->
    <FondoAnimado />

    <!-- 🧠 Lista de intereses -->
    <ul class="contenedor-lista">
      <li class="item" v-for="interes in intereses" :key="interes">
        {{ interes }}
      </li>
    </ul>
  </div>
</template>

<style scoped>
.intereses-contenedor {
  position: relative;
  margin: 0 auto;
  max-width: 85%;
  padding: 2rem;
  border-radius: 1rem;
  overflow: hidden;
  background: rgba(10, 10, 30, 0.45); /* más integrado con el fondo aurora */
  backdrop-filter: blur(10px) brightness(1.2);
  box-shadow: 0 4px 25px rgba(0, 0, 0, 0.5);
}

/* Ajuste para el SVG del fondo animado */
.intereses-contenedor :deep(svg) {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  border-radius: inherit;
  opacity: 0.8;
}

.contenedor-lista {
  list-style-type: none;
  padding: 1rem;
  color: #e9f1ff;
  font-size: 1.25rem;
  line-height: 1.7;
  text-shadow: 1px 1px 4px rgba(0, 0, 0, 0.6);
  z-index: 1;
  position: relative;
  font-weight: 400;
}

.item {
  margin-bottom: 1rem;
  transition: transform 0.3s ease, color 0.3s ease, text-shadow 0.3s ease;
}

.item:hover {
  transform: translateX(6px);
  color: #00f5d4;
  text-shadow: 0 0 10px #00f5d4;
}
</style>
