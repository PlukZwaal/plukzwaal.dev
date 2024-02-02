<template>
  <header class="wrapper">
    <div class="mobile-header">
      <h1>P.</h1>
      <div class="menu" :class="{ 'cross': isMobileMenuOpen }" @click="toggleMenu">
        <div class="bar"></div>
        <div class="bar"></div>
        <div class="bar"></div>
      </div>
    </div>
    <div class="desktop-menu">
      <h1>P.</h1>
      <div>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/projects">Projects</RouterLink>
        <RouterLink to="/contact">Contact</RouterLink>
      </div>
    </div>
    <div v-if="isMobileMenuOpen" class="mobile-menu">
      <RouterLink to="/" @click="closeMobileMenu">Home</RouterLink>
      <RouterLink to="/about" @click="closeMobileMenu">About</RouterLink>
      <RouterLink to="/projects" @click="closeMobileMenu">Projects</RouterLink>
      <RouterLink to="/contact" @click="closeMobileMenu">Contact</RouterLink>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue'
import { RouterLink } from 'vue-router'

const isMobileMenuOpen = ref(false)

const toggleMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}
const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}
</script>

<style scoped>
/* GENERAL */

/* ---------------------------------------------- */
/* DESKTOP */
/* ---------------------------------------------- */

.desktop-menu,
.mobile-header{
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 100px;
}

/* ---------------------------------------------- */
/* MOBILE */
/* ---------------------------------------------- */

.mobile-menu {
  display: flex;
  flex-direction: column;
  position: absolute;
  left: 0;
  background-color: #fff;
  width: 100%;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.bar {
  width: 30px;
  height: 3px;
  background-color: #333;
  margin: 6px 0;
  transition: 0.4s;
}

.cross .bar:nth-child(1) {
  transform: rotate(-45deg) translate(-5px, 6px);
}

.cross .bar:nth-child(2) {
  opacity: 0;
}

.cross .bar:nth-child(3) {
  transform: rotate(45deg) translate(-5px, -6px);
}

/* ---------------------------------------------- */
/* MEDIA QUERIES */
/* ---------------------------------------------- */

@media (max-width: 768px) {
  .desktop-menu {
    display: none;
  }

  .mobile-header {
    display: flex;
  }
}

@media (min-width: 768px) {
  .desktop-menu {
    display: flex;
  }

  .mobile-header {
    display: none;
  }
}
</style>
