<script setup lang="ts">
import nlwUniteIcon from '../assets/nlw-unite-icon.svg'
import NavLink from './NavLink.vue'
</script>

<template>
  <header class="flex items-center gap-5 py-2">
    <img :src="nlwUniteIcon" />

    <nav class="flex items-center gap-5">
      <NavLink href="/eventos">Eventos</NavLink>
      <NavLink href="/participantes">Participantes</NavLink>
    </nav>
  </header>
</template>

<style scoped></style>
