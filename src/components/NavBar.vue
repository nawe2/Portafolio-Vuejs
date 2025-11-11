<template>
  <nav class="navbar">
    <div class="nav-inner">
      <ul class="nav-list">
        <li v-for="nav in navegacion" :key="nav.id" class="nav-item">
          <a
            :href="nav.enlace"
            class="nav-link"
            :class="{ active: currentHash === nav.enlace }"
          >
            {{ nav.nombre }}
          </a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const navegacion = ref([
  { id: 1, nombre: 'Sobre mí',     enlace: '#datos' },
  { id: 2, nombre: 'Proyectos',    enlace: '#proyectos' },
  { id: 3, nombre: 'Habilidades',  enlace: '#skills' },
  { id: 4, nombre: 'Educación',    enlace: '#educacion' },
  { id: 5, nombre: 'Experiencia',  enlace: '#experiencia' }
])

// resalta link activo según el hash
const currentHash = ref(window.location.hash || '#datos')
const onHashChange = () => { currentHash.value = window.location.hash || '#datos' }

onMounted(() => window.addEventListener('hashchange', onHashChange))
onBeforeUnmount(() => window.removeEventListener('hashchange', onHashChange))
</script>

<style scoped>
:root{
  --nav-bg: rgba(10, 25, 47, 0.7);   /* azul translúcido */
  --nav-border: rgba(97, 218, 251, 0.15);
  --nav-text: #e9f1ff;
  --nav-accent: #61dafb;             /* celeste sutil */
  --nav-hover-bg: rgba(97, 218, 251, 0.08);
}

.navbar{
  position: sticky;
  top: 0;
  z-index: 50;
  backdrop-filter: blur(8px);
  background: var(--nav-bg);
  border-bottom: 1px solid var(--nav-border);
}

/* contenedor */
.nav-inner{
  max-width: 1100px;
  margin: 0 auto;
  padding: 10px 16px;
}

/* lista horizontal */
.nav-list{
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  list-style: none;
  padding: 0;
  margin: 0;
  justify-content: flex-end;
}

/* link minimal con subrayado animado */
.nav-link{
  position: relative;
  display: inline-block;
  padding: 6px 10px;
  border-radius: 8px;
  color: var(--nav-text);
  text-decoration: none;
  transition: background .2s ease, color .2s ease, transform .2s ease;
}

.nav-link::after{
  content: "";
  position: absolute;
  left: 10px;
  right: 10px;
  bottom: 4px;
  height: 2px;
  border-radius: 2px;
  background: transparent;
  transition: background .2s ease, transform .2s ease, opacity .2s ease;
  opacity: 0;
  transform: scaleX(0.6);
}

.nav-link:hover{
  background: var(--nav-hover-bg);
  transform: translateY(-1px);
}

.nav-link:hover::after{
  background: var(--nav-accent);
  opacity: .9;
  transform: scaleX(1);
}

/* estado activo por hash */
.nav-link.active{
  background: var(--nav-hover-bg);
}
.nav-link.active::after{
  background: var(--nav-accent);
  opacity: 1;
  transform: scaleX(1);
}

/* móvil: centrado y mayor click area */
@media (max-width: 768px){
  .nav-inner{ padding: 10px 12px; }
  .nav-list{ justify-content: center; gap: 6px; }
  .nav-link{ padding: 8px 12px; }
}
</style>
