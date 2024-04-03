<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <main class="bg-slate-800 min-h-screen flex justify-center items-center gap-16">
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <RouterView />
  </main>
</template>

<style scoped></style>
