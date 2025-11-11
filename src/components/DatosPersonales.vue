<script setup>

import perfil from '/src/assets/custom/imagenperfil.png'
import instagram from '/src/assets/instagram_icon.svg'
import github from '/src/assets/github_icon.svg'
import cv from '/src/assets/cv_resume_icon.svg'

const title = "Nahuel Spikerman"
const residencia = "Mar del Plata, Argentina"
const presentacion =
  "Hola, soy Nahuel Spikerman, estudiante de la tecnicatura en programación en la Universidad Nacional Tecnológica y estudiante de Ingeniería en informática en la Universidad Nacional de Mar del Plata."

const redesSociales = [
  { id: 1, name: "instagram", src: instagram, url: "https://www.instagram.com/nahuel_spikerman" },
  { id: 2, name: "github", src: github, url: "https://github.com/nawe2" },
  { id: 3, name: "curriculum", src: cv, url: "#" }
]

const telefono = "+54 9 2234233114"
</script>

<template>
  <section class="datos-personales">
    <div class="card fancy">
      <img class="perfil-img ring" :src="perfil" alt="Foto de perfil" />
      <div class="info">
        <h1 class="titulo">{{ title }}</h1>
        <p class="descripcion">{{ presentacion }}</p>

        <ul class="container-lista">
          <li v-for="red in redesSociales" :key="red.id">
            <a class="social-btn" :href="red.url" target="_blank" rel="noopener">
              <img class="icon-redsocial" :src="red.src" width="28" :alt="red.name" />
            </a>
          </li>
        </ul>
        <h3 class="pill phone">☎ Mi Teléfono personal: {{ telefono }}</h3>
        <h4 class="pill location">{{ residencia }}</h4>
      </div>
    </div>
  </section>
</template>

<style scoped>
:root {
  --bg-card: rgba(10, 25, 47, 0.78);
  --bg-chip: rgba(255, 255, 255, 0.08);
  --text-main: #e9f1ff;
  --text-soft: #c9d8eb;
  --accent: #61dafb;          /* celeste */
  --accent-2: #00f5d4;        /* turquesa sutil */
}

/* Layout base */
.datos-personales {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 2.5rem 1.25rem;
}

/* Card “glass” con borde degradado sutil */
.card {
  position: relative;
  display: flex;
  gap: 2rem;
  align-items: center;
  max-width: 980px;
  width: 100%;
  padding: 2rem;
  border-radius: 18px;
  background: var(--bg-card);
  backdrop-filter: blur(10px);
  color: var(--text-main);
  box-shadow: 0 12px 35px rgba(0,0,0,.45);
  overflow: hidden;
  transition: box-shadow .25s ease;
}
.card.fancy::before {
  content: "";
  position: absolute;
  inset: -1px;
  z-index: -1;
  border-radius: 20px;
  background: linear-gradient(135deg,
    rgba(97,218,251,.45),
    rgba(0,245,212,.3),
    rgba(97,218,251,.1));
  filter: blur(6px);
}
.card:hover { box-shadow: 0 16px 40px rgba(0,0,0,.55); }

/* Imagen con anillo/halo */
.perfil-img {
  width: 150px;
  height: 150px;
  border-radius: 999px;
  object-fit: cover;
}
.ring {
  position: relative;
  box-shadow:
    0 0 0 3px rgba(255,255,255,.08),
    0 6px 24px rgba(0,0,0,.45);
}
.ring::after {
  content: "";
  position: absolute;
  inset: -6px;
  border-radius: 999px;
  background: radial-gradient(70% 70% at 30% 30%,
    rgba(97,218,251,.25),
    rgba(0,245,212,.1) 60%,
    transparent 70%);
  z-index: -1;
}

/* Texto */
.info { flex: 1; text-align: center; }
.titulo {
  font-size: 2rem;
  margin: 0 0 .75rem;
  line-height: 1.1;
  letter-spacing: .3px;
}
.descripcion {
  font-size: 1.06rem;
  color: var(--text-soft);
  margin-bottom: 1.25rem;
}

/* Redes sociales como botones */
.container-lista {
  display: flex;
  justify-content: center;
  gap: .6rem;
  list-style: none;
  padding: 0;
  margin: 0 0 1.1rem;
}
.social-btn {
  display: grid;
  place-items: center;
  width: 40px; height: 40px;
  border-radius: 999px;
  background: var(--bg-chip);
  border: 1px solid rgba(97,218,251,.2);
  transition: transform .2s ease, box-shadow .25s ease, background .25s ease, border-color .25s ease;
}
.social-btn:hover {
  transform: translateY(-2px);
  background: rgba(97,218,251,.12);
  box-shadow: 0 0 14px rgba(97,218,251,.25);
  border-color: rgba(97,218,251,.45);
}
.icon-redsocial { display: block; width: 22px; height: 22px; }

/* Pills (teléfono / residencia) */
.pill {
  display: inline-block;
  margin: .25rem 0;
  padding: .5rem .9rem;
  border-radius: 999px;
  background: var(--bg-chip);
  border: 1px solid rgba(97,218,251,.18);
}
.phone { color: #ffdca8; font-weight: 600; }
.location { color: #b5c9e6; }

h3, h4 { margin: .35rem 0; font-size: 1rem; font-weight: 500; }

/* Responsive */
@media (max-width: 820px) {
  .card { flex-direction: column; padding: 1.6rem; gap: 1.2rem; }
  .perfil-img { width: 120px; height: 120px; }
  .titulo { font-size: 1.7rem; }
  .descripcion { font-size: 1rem; }
}
</style>
