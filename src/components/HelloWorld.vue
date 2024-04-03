<script setup lang="ts">
defineProps<{ msg: string }>()
</script>

<template>
  <h1 class="font-semibold text-3xl text-slate-300">{{ msg }}</h1>
</template>

<style scoped></style>
