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
            <div>
                <p @click="switchTheme"><img id="themeIcon" src="" alt=""></p>
            </div>
        </div>
    </header>
</template>

<script setup>
import { ref } from 'vue';
import { onMounted } from 'vue'

onMounted(() => {
    changeTheme();
})

const switchTheme = () => {
    localStorage.setItem('theme', localStorage.getItem('theme') === 'light' ? 'dark' : 'light');
    changeTheme();
};

const changeTheme = () => {
    if (localStorage.getItem('theme') === 'light') {
        document.documentElement.style.setProperty('--background-color-primary', 'var(--light-background-color-primary)');
        document.documentElement.style.setProperty('--background-color-transparent-primary', 'var(--light-background-color-transparent-primary)');
        document.documentElement.style.setProperty('--text-primary-color', 'var(--light-text-primary-color)');
        document.getElementById('themeIcon').src = 'src/assets/images/sun.svg';
    } else {
        document.documentElement.style.setProperty('--background-color-primary', 'var(--dark-background-color-primary)');
        document.documentElement.style.setProperty('--background-color-transparent-primary', 'var(--dark-background-color-transparent-primary)');
        document.documentElement.style.setProperty('--text-primary-color', 'var(--dark-text-primary-color)');
        document.getElementById('themeIcon').src = 'src/assets/images/moon.svg';
    }
}

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

a.router-link-active {
    font-weight: bold;
}

.hamburger {
    display: none;
}

nav {
    display: flex;
    gap: 20px;
}

img {
    width: 30px;
    height: 30px;
    z-index: 3;
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
        background-color: var(--background-color-transparent-primary);
        flex-direction: column;
        justify-content: center;
        align-items: center;
        z-index: 1;
        font-size: 2.5rem
    }

    nav.open {
        display: flex;
    }
}
</style>
