<template>
  <!-- Fondo SVG animado tipo "Aurora líquida" -->
  <svg preserveAspectRatio="xMidYMid slice" viewBox="0 0 100 100">
    <!-- Capa 1: base en tonos púrpura -->
    <path
      fill="url(#grad1)"
      class="blob blob1"
      d="M42.5,-62.4C54.9,-54.1,63.8,-43.3,69.3,-30.6C74.8,-17.9,76.9,-3.5,72.3,8.5C67.6,20.5,56.3,30,46.3,41.7C36.3,53.5,27.5,67.4,14.8,70.4C2.1,73.4,-14.4,65.6,-29.6,57.3C-44.7,49,-58.5,40.1,-63.3,27.4C-68.1,14.7,-63.8,-1.8,-58.5,-16.2C-53.1,-30.6,-46.8,-42.8,-36.9,-52.2C-27,-61.6,-13.5,-68.1,0.6,-68.9C14.7,-69.7,29.3,-64.8,42.5,-62.4Z"
      transform="translate(50 50)"
    />

    <!-- Capa 2: color turquesa -->
    <path
      fill="url(#grad2)"
      class="blob blob2"
      d="M33.6,-50.5C46.5,-44.6,61.6,-40.5,68.2,-30.3C74.8,-20.2,72.9,-4.1,67.9,9.8C62.9,23.7,54.8,35.5,43.8,44.3C32.8,53.1,18.9,58.9,5.3,57.7C-8.2,56.6,-16.4,48.6,-28.1,42.1C-39.8,35.7,-55,30.8,-60.4,20.5C-65.7,10.3,-61.3,-5.3,-53.6,-17.2C-45.8,-29.2,-34.8,-37.5,-24.1,-45.5C-13.3,-53.5,-2.7,-61.3,8.6,-62.3C19.8,-63.3,31.6,-57.4,33.6,-50.5Z"
      transform="translate(50 50)"
    />

    <!-- Definición de gradientes -->
    <defs>
      <radialGradient id="grad1" cx="50%" cy="50%" r="70%">
        <stop offset="0%" stop-color="#9b5de5" />
        <stop offset="100%" stop-color="#f15bb5" />
      </radialGradient>

      <radialGradient id="grad2" cx="50%" cy="50%" r="80%">
        <stop offset="0%" stop-color="#00bbf9" />
        <stop offset="100%" stop-color="#00f5d4" />
      </radialGradient>
    </defs>
  </svg>
</template>

<style scoped>
svg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  overflow: hidden;
  background: radial-gradient(circle at 30% 50%, #0d1321, #000814);
}

/* Animaciones */
@keyframes rotate {
  0% { transform: rotate(0deg) scale(1); }
  50% { transform: rotate(180deg) scale(1.05); }
  100% { transform: rotate(360deg) scale(1); }
}

@keyframes counterrotate {
  0% { transform: rotate(360deg) scale(1); }
  50% { transform: rotate(180deg) scale(1.1); }
  100% { transform: rotate(0deg) scale(1); }
}

.blob1 {
  animation: rotate 45s linear infinite;
  opacity: 0.7;
  transform-origin: center;
}

.blob2 {
  animation: counterrotate 60s linear infinite;
  opacity: 0.6;
  transform-origin: center;
}
</style>
