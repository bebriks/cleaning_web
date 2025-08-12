<template>
  <v-app class="v_app">
    <router-view />
  </v-app>
</template>

<script setup lang="ts">
  import AOS from 'aos'
  import { onMounted } from 'vue'
  onMounted(() => {
    AOS.init()
  })
</script>

<style>

</style>
