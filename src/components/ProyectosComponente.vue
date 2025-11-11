<script setup>
import { ref } from 'vue'

// Importa imágenes

import custom1 from '/src/assets/custom/proyecto1.png'
import custom2 from '/src/assets/custom/proyecto2.png'

// Lista reactiva de proyectos
const misProyectos = ref([
  {
    id: 1,
    src: custom1,
    titulo: "Proyecto sin título",
    descripcion: "Proyecto integrador PSeint",
    projectoLink: "#",
    githubLink: ""
  },
  {
    id: 2,
    src: custom2,
    titulo: "Proyecto Java",
    descripcion: "Juego del ahorcado en java",
    projectoLink: "#",
    githubLink: ""
  }
])
</script>

<template>
  <div class="galeria">
    <div v-for="proyecto in misProyectos" :key="proyecto.id" class="proyecto">
      <img :src="proyecto.src" :alt="proyecto.titulo" />
      <div class="proyecto-info">
        <h3>{{ proyecto.titulo }}</h3>
        <p>{{ proyecto.descripcion }}</p>
        <div class="proyecto-links">
          <a class="btn-ver-mas" :href="proyecto.projectoLink" target="_blank">Ver más</a>
          <a v-if="proyecto.githubLink" class="github-link" :href="proyecto.githubLink" target="_blank">
            Ver en GitHub
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.galeria {
  width: 100%;
  height: 100%;
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  padding: 20px;
  justify-content: center;
  background: linear-gradient(-45deg, var(--fondo-secundario), var(--fondo-principal));
  background-size: 400% 400%;
  animation: gradient 15s ease infinite;
}

@keyframes gradient {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

.proyecto {
  display: flex;
  flex-direction: column;
  border: 2px solid #ddd;
  border-radius: 8px;
  overflow: hidden;
  background-color: #f9f9f9;
  max-width: 222px;
  flex: 1 1 300px;
}

.proyecto img {
  width: 100%;
  height: auto;
  display: block;
}

.proyecto-info {
  padding: 15px;
  text-align: center;
}

.proyecto-info h3 {
  margin: 10px 0;
  font-size: 1.3em;
  color: #333;
}

.proyecto-info p {
  margin: 10px 0;
  font-size: 1em;
  color: #666;
}

.proyecto-links {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-top: 30px;
}

.proyecto-links .btn-ver-mas {
  background-color: #007BFF;
  color: #fff;
  padding: 10px 15px;
  border-radius: 5px;
  text-decoration: none;
  transition: background-color 0.3s;
  margin-top: 1rem;
}

.proyecto-links .btn-ver-mas:hover {
  background-color: #0056b3;
}

.proyecto-links .github-link {
  color: #333;
  text-decoration: none;
  font-size: 0.9em;
}

.proyecto-links .github-link:hover {
  text-decoration: underline;
}
</style>
