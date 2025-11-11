<script setup>
import img1 from '/src/components/icons/js.svg';
import img2 from '/src/components/icons/python.svg';
import img3 from '/src/components/icons/html-css.svg';
import img4 from '/src/components/icons/java.svg';
import img5 from '/src/components/icons/sql.svg';
import img7 from '/src/components/icons/vue.svg';
import img11 from '/src/components/icons/git.svg';
import img15 from '/src/components/icons/visual.svg';
import img17 from '/src/components/icons/mysql.svg';
import img19 from '/src/components/icons/arg.svg';
import img20 from '/src/components/icons/eeuu.svg';

//Se importa ref de vue para poder usarlo
import { ref } from 'vue';
//Se crea un array de objetos con las habilidades
//Este es un array de objetos con habilidades que se pueden modificar o agregar
const habilidades = ref([
    {// Se crea un objeto con id, nombre y habilidades
        id: 1, nombre: 'Lenguajes de Programación', habilidades: [
            //Se crea un objeto con id, nombre, nivel e icono
            { id: 1, nombre: 'JavaScript', nivel: 'Avanzado', icono: img1 },
            { id: 2, nombre: 'Python', nivel: 'Intermedio', icono: img2 },
            { id: 3, nombre: 'HTML/CSS', nivel: 'Intermedio', icono: img3 },
            { id: 4, nombre: 'Java', nivel: 'Avanzado', icono: img4 },
            { id: 5, nombre: 'SQL', nivel: 'Intermedio', icono: img5 }
        ]
    },
    {
        id: 2, nombre: 'Frameworks y Librerías', habilidades: [
            { id: 1, nombre: 'Vue.js', nivel: 'Intermedio', icono: img7 },
        ]
    },
    {
        id: 3, nombre: 'Herramientas y Software', habilidades: [
            { id: 1, nombre: 'Git', nivel: 'Avanzado', icono: img11 },
            { id: 2, nombre: 'Visual Studio Code', nivel: 'Avanzado', icono: img15 }
        ]
    },
    {
        id: 4, nombre: 'Bases de Datos', habilidades: [
            { id: 2, nombre: 'MySQL', nivel: 'Intermedio', icono: img17 },
        ]
    },
    {
        id: 5, nombre: 'Idiomas', habilidades: [
            { id: 1, nombre: 'Español', nivel: 'Nativo', icono: img19 },
            { id: 2, nombre: 'Inglés', nivel: 'Avanzado (C1)', icono: img20 }
        ]
    }
]);

</script>


<template>
    <!--Este componente vue funciona de esta forma:-->
    <div class="skills-contenedor">
        <!--Se recorre el array habilidades con v-for y se asigna la key habilidad.id-->
        <div v-for="habilidad in habilidades" :key="habilidad.id" class="skills-categoria">
            <!--Se muestra el nombre de la habilidad-->
            <h3>{{ habilidad.nombre }}</h3>
            <ul class="skills">
                <!--Se recorre el array habilidades con v-for y se asigna la key habilidad.id-->
                <li v-for="habilidad in habilidad.habilidades" :key="habilidad.id" class="skill">
                    <!--Se muestra el icono de la habilidad y el nombre de la habilidad con su nivel-->
                    <img :src="habilidad.icono" :alt="habilidad.nombre">
                    <!--Se muestra el icono de la habilidad y el nombre de la habilidad con su nivel-->
                    <span>{{ habilidad.nombre }}: {{ habilidad.nivel }}</span>
                </li>
            </ul>
        </div>
    </div>

</template>

<style scoped>
.skills-contenedor {
  position: relative;
  padding: 3rem 2rem;
  border-radius: 1rem;
  background: radial-gradient(circle at 30% 50%, #0d1b2a, #000814);
  box-shadow: inset 0 0 40px rgba(0, 255, 255, 0.05);
  overflow: hidden;
}

/* Título de cada categoría */
.skills-categoria {
  margin-bottom: 2rem;
  backdrop-filter: blur(6px);
}

.skills-categoria h3 {
  font-size: 1.6rem;
  color: #00f5d4;
  margin-bottom: 1.2rem;
  font-weight: 600;
  letter-spacing: 0.5px;
  border-left: 4px solid #00f5d4;
  padding-left: 10px;
}

/* Contenedor de las skills */
.skills {
  display: flex;
  flex-wrap: wrap;
  gap: 1.2rem;
  justify-content: flex-start;
}

/* Cada skill como card */
.skill {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 0.8rem 1.2rem;
  border-radius: 12px;
  background: rgba(255, 255, 255, 0.08);
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
  transition: all 0.3s ease;
  cursor: default;
}

.skill:hover {
  transform: translateY(-3px);
  background: rgba(0, 245, 212, 0.15);
  box-shadow: 0 0 15px rgba(0, 245, 212, 0.4);
}

/* Icono */
.skill img {
  width: 32px;
  height: 32px;
  filter: drop-shadow(0 0 4px rgba(0, 245, 212, 0.2));
}

/* Texto */
.skill span {
  color: #e0e0e0;
  font-size: 1rem;
  font-weight: 400;
}

/* Responsive */
@media (max-width: 768px) {
  .skills-categoria h3 {
    text-align: center;
  }

  .skills {
    justify-content: center;
  }

  .skill {
    flex: 1 1 250px;
    justify-content: center;
  }
}
</style>
