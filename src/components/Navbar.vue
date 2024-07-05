<template>
    <header>
        <div class="wrapper">
            <div class="hamburger" @click="toggleMenu">{{ isMenuOpen ? '✖' : '☰' }}</div>
            <nav :class="{ open: isMenuOpen }">
                <RouterLink to="/" @click="closeMenu">Home</RouterLink>
                <RouterLink to="/about" @click="closeMenu">About</RouterLink>
                <RouterLink to="/projects" @click="closeMenu">Projects</RouterLink>
                <RouterLink to="/contact" @click="closeMenu">Contact</RouterLink>
            </nav>
        </div>
    </header>
</template>

<script setup>
import { ref } from 'vue';

const isMenuOpen = ref(false);

const toggleMenu = () => {
    isMenuOpen.value = !isMenuOpen.value;
};

const closeMenu = () => {
    isMenuOpen.value = false;
};
</script>

<style scoped>
.wrapper {
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 100%;
}

header {
    height: 100px;
}

a {
    text-decoration: none;
    color: var(--text-primary-color);
}

.hamburger {
    display: none;
}

nav {
    display: flex;
    gap: 20px;
}

@media (max-width: 768px) {
    .hamburger {
        display: block;
        font-size: 30px;
        cursor: pointer;
        z-index: 2;
    }

    nav {
        display: none;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(255, 255, 255, 0.75);
        flex-direction: column;
        justify-content: center;
        align-items: center;
        z-index: 1;
    }

    nav.open {
        display: flex;
    }
}
</style>
