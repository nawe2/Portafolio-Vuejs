<script setup>
import icono1 from '/src/assets/game-development-icon.svg'
import icono2 from '/src/assets/circular.svg'
import { ref } from 'vue'

const titulo = 'Desarrollador de Videojuegos'
const fecha = '2023 — Actualidad'

const experiencias = ref([
  {
    id: 1,
    src: icono1,
    titulo: 'Diseño y Programación de Juegos',
    parrafo:
      'Participo en el desarrollo de mecánicas y sistemas de juego usando Unity y C#, enfocándome en la optimización, físicas y lógica del gameplay.'
  },
  {
    id: 2,
    src: icono2,
    titulo: 'Integración y Publicación',
    parrafo:
      'Trabajo en la integración de assets, efectos visuales y pipelines de publicación, además de testing en distintas plataformas y automatización de builds.'
  }
])
</script>

<template>
  <section class="experiencia-section">
    <div class="card">
      <div class="header">
        <h3 class="titulo">{{ titulo.toUpperCase() }}</h3>
        <p class="fecha">{{ fecha }}</p>
      </div>

      <div class="experiencias">
        <div class="item" v-for="exp in experiencias" :key="exp.id">
          <div class="icono">
            <img :src="exp.src" alt="icono experiencia" />
          </div>
          <div class="info">
            <h4>{{ exp.titulo }}</h4>
            <p>{{ exp.parrafo }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.experiencia-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  color: #e9f1ff;
  font-family: 'Poppins', sans-serif;
  border: none !important;
}
.experiencia-section::before,
.experiencia-section::after,
.experiencia-section hr {
  display: none !important;
}

/* Tarjeta principal */
.card {
  width: 90%;
  max-width: 950px;
  background: rgba(10, 25, 47, 0.8);
  border-radius: 20px;
  padding: 2rem;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.35);
  backdrop-filter: blur(10px);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}
.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.45);
}

/* Cabecera */
.header {
  text-align: center;
  margin-bottom: 2rem;
}
.titulo {
  font-size: 1.6rem;
  color: #61dafb; /* celeste estilo React */
  margin-bottom: 0.3rem;
  letter-spacing: 0.6px;
  font-weight: 700;
}
.fecha {
  color: #9fd3ff;
  font-size: 1rem;
}

/* Experiencias */
.experiencias {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.5rem;
}
@media (max-width: 768px) {
  .experiencias {
    grid-template-columns: 1fr;
  }
}

/* Tarjetas individuales */
.item {
  background: rgba(255, 255, 255, 0.06);
  border-radius: 15px;
  padding: 1.5rem;
  text-align: center;
  border: 1px solid rgba(97, 218, 251, 0.15);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}
.item:hover {
  transform: translateY(-4px);
  box-shadow: 0 0 20px rgba(97, 218, 251, 0.25);
}

/* Icono */
.icono {
  background: linear-gradient(145deg, #0a2342, #0b3149);
  border-radius: 50%;
  padding: 1rem;
  margin: 0 auto 1rem;
  width: 75px;
  height: 75px;
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: 0 0 15px rgba(97, 218, 251, 0.15);
}
.icono img {
  width: 45px;
  height: 45px;
}

/* Texto */
.info h4 {
  color: #89c9ff;
  font-size: 1.1rem;
  margin-bottom: 0.6rem;
  font-weight: 600;
}
.info p {
  font-size: 0.95rem;
  color: #d4e2f0;
  line-height: 1.6;
}
</style>
