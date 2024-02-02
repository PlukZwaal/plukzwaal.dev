<script setup>
import { RouterView } from 'vue-router'
import HeaderComponent from './assets/components/HeaderComponent.vue'
</script>

<template>
  <HeaderComponent />
  <div class="wrapper">
    <RouterView />
  </div>
</template>