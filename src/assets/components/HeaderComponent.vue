<template>
  <header>
    <div class="wrapper">
      <div class="desktop-menu">
        <h1>
          <RouterLink to="/">P.</RouterLink>
        </h1>
        <div>
          <RouterLink to="/about">About</RouterLink>
          <RouterLink to="/projects">Projects</RouterLink>
          <RouterLink to="/contact">Contact</RouterLink>
        </div>
      </div>
      <div class="mobile-header">
        <h1>
          <RouterLink to="/" @click="closeMobileMenu">P.</RouterLink>
        </h1>
        <div class="menu" :class="{ 'cross': isMobileMenuOpen }" @click="toggleMenu">
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
        </div>
      </div>
      <div v-if="isMobileMenuOpen" class="mobile-menu">
        <RouterLink to="/about" @click="closeMobileMenu">About</RouterLink>
        <RouterLink to="/projects" @click="closeMobileMenu">Projects</RouterLink>
        <RouterLink to="/contact" @click="closeMobileMenu">Contact</RouterLink>
      </div>
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

a {
  text-decoration: none;
  padding: 10px;
  color: #000000;
}

.desktop-menu,
.mobile-header {
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
  background-color: #ffffff;
  margin-left: -20pX;
  width: 100%;
  height: calc(100vh - 100px);
}

.mobile-menu a {
  padding-left: 30px;
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
