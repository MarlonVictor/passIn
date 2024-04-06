<script setup lang="ts">
import Header from '../components/Header.vue'
import AttendeeList from '../components/AttendeeList.vue'
</script>

<template>
  <div id="home" class="max-w-[76rem] mx-auto py-5 flex flex-col gap-5">
    <Header />
    <AttendeeList msg="oi" />
  </div>
</template>

<style scoped></style>
