<script setup lang="ts">
import { Search } from 'lucide-vue-next'

defineProps<{ msg: string }>()
</script>

<template>
  <div class="flex gap-3 items-center">
    <h1 class="text-2xl font-bold">Participantes</h1>

    <div
      class="flex items-center gap-3 w-72 h-9 px-3 py-1.5 bg-transparent border border-white/10 rounded-lg text-sm"
    >
      <Search class="size-4 text-emerald-200" />
      <input placeholder="Buscar participante..." class="flex-1 bg-transparent outline-none" />
    </div>
  </div>
  <!-- <h1 class="font-semibold text-3xl text-slate-300">{{ msg }}</h1> -->
</template>

<style scoped></style>
