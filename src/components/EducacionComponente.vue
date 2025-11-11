<script setup>
import { ref } from 'vue'

const timeline = ref([
  {
    fecha: '2025',
    titulo: 'Técnicatura Universitaria en Programación',
    descripcion: 'Aprendizaje de lenguajes como Python, Java, JavaScript, HTML, CSS y más.',
    color: '#4F8EF7'
  },
  {
    fecha: '2023',
    titulo: 'Proyecto Personal - Videojuego 2D en Unity',
    descripcion: 'Desarrollé un videojuego 2D completo con C#, gestionando assets, animaciones, UI y lógica de niveles.',
    color: '#0EA5E9'
  },
  {
    fecha: '2022',
    titulo: 'Curso de Bases de Datos',
    descripcion: 'Aprendí SQL y modelado de datos relacionales aplicados a sistemas reales.',
    color: '#EC4899'
  },
  {
    fecha: '2021',
    titulo: 'Curso Avanzado de Desarrollo de Videojuegos',
    descripcion: 'Profundicé en programación de gameplay y optimización en Unity, abarcando físicas, shaders y patrones de arquitectura aplicados a juegos.',
    color: '#EAB308'
  },
  {
    fecha: '2020',
    titulo: 'Introducción a la Ingeniería en Informática',
    descripcion: 'Completé un curso online sobre fundamentos de programación con Pascal y C.',
    color: '#10B981'
  }
])
</script>

<template>
  <section class="timeline" id="educacion">
    <div class="linea">
      <div
        v-for="(item, index) in timeline"
        :key="index"
        class="evento"
        :class="{ izquierda: index % 2 === 0, derecha: index % 2 !== 0 }"
      >
        <div class="contenido" :style="{ borderColor: item.color }">
          <span class="fecha" :style="{ backgroundColor: item.color }">{{ item.fecha }}</span>
          <h3>{{ item.titulo }}</h3>
          <p>{{ item.descripcion }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.timeline {
  width: 90%;
  max-width: 900px;
  margin: 3rem auto;
  position: relative;
  font-family: "Poppins", sans-serif;
  border: none !important;
}
.timeline::before,
.timeline::after,
.timeline hr {
  content: none !important;
  display: none !important;
}

/* Título */
h2 {
  text-align: center;
  color: #fff;
  font-size: 2rem;
  margin-bottom: 2rem;
}

/* Línea vertical */
.linea {
  position: relative;
  margin: 0 auto;
  padding: 2rem 0;
}
.linea::before {
  content: "";
  position: absolute;
  width: 4px;
  background: rgba(255, 255, 255, 0.2);
  top: 0;
  bottom: 2rem; /* evita que baje de más */
  left: 50%;
  transform: translateX(-50%);
}

/* Eventos */
.evento {
  position: relative;
  width: 50%;
  padding: 1rem 2rem;
}
.evento.izquierda {
  left: 0;
  text-align: right;
}
.evento.derecha {
  left: 50%;
  text-align: left;
}

/* Contenido */
.contenido {
  position: relative;
  background: rgba(255, 255, 255, 0.05);
  border-left: 4px solid;
  backdrop-filter: blur(6px);
  padding: 1.5rem;
  border-radius: 10px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}
.izquierda .contenido {
  border-left: none;
  border-right: 4px solid;
}
.contenido:hover {
  transform: translateY(-5px);
  box-shadow: 0 0 15px rgba(255, 255, 255, 0.15);
}

/* Fecha */
.fecha {
  display: inline-block;
  color: #fff;
  font-weight: 700;
  padding: 0.3rem 1rem;
  border-radius: 20px;
  margin-bottom: 0.8rem;
}

/* Títulos y texto */
h3 {
  color: #fff;
  margin-bottom: 0.5rem;
}
p {
  color: #cbd5e1;
  font-size: 0.95rem;
  line-height: 1.5;
}

/* Círculos */
.evento::after {
  content: "";
  position: absolute;
  top: 1.5rem;
  width: 15px;
  height: 15px;
  background: #fff;
  border: 3px solid #1e293b;
  border-radius: 50%;
  z-index: 2;
}
.evento.izquierda::after {
  right: -8px;
}
.evento.derecha::after {
  left: -8px;
}

/* Responsive */
@media (max-width: 768px) {
  .linea::before {
    left: 8px;
  }
  .evento {
    width: 100%;
    padding-left: 2rem;
  }
  .evento.izquierda,
  .evento.derecha {
    left: 0;
    text-align: left;
  }
  .evento::after {
    left: 0;
  }
}
</style>
