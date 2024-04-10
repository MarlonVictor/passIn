<script setup lang="ts">
interface IconButtonProps {
  transparent?: boolean
}

const { transparent } = defineProps<IconButtonProps>()
</script>

<template>
  <button
    class="border border-white/10 rounded-md p-1.5 transition hover:brightness-200 disabled:cursor-not-allowed disabled:opacity-50 disabled:hover:brightness-100"
    :class="transparent ? 'bg-black/20' : 'bg-white/10'"
  >
    <slot></slot>
  </button>
</template>

<style scoped></style>
