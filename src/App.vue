<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <RouterView />
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@400;600&display=swap');

html {
  height: 100%;
}

body,
main {
  min-height: 100vh;
  font-family: 'Outfit', sans-serif;
}
</style>