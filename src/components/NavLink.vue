<script setup lang="ts">
import { defineProps } from 'vue'

interface NavLinkProps {
  href: string
}

const { href } = defineProps<NavLinkProps>()
</script>

<template>
  <a :href="href" class="font-semibold text-sm">
    <slot></slot>
  </a>
</template>

<style scoped></style>
