<script setup lang="ts">
interface IconButtonProps {
  transparent?: boolean
}

const { transparent } = defineProps<IconButtonProps>()
</script>

<template>
  <button
    class="border border-white/10 rounded-md p-1.5 transition hover:brightness-200"
    :class="transparent ? 'bg-black/20' : 'bg-white/10'"
  >
    <slot></slot>
  </button>
</template>

<style scoped></style>
