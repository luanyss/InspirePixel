<script setup>
import logo from "../assets/logo.png"
import { ref } from 'vue'
import { Icon } from '@iconify/vue'; // Importa a peça do brinquedo

const isDarkMode = ref(false)

const toggleDarkMode = () => {
    isDarkMode.value = !isDarkMode.value
    document.body.classList.toggle('dark-mode')
}
</script>

<template>
    <header>
        <div class="header-container">
            <img :src="logo" alt="Logo" class="logo">
<!-- <nav>
        <Icon icon="material-symbols:search" width="24" />

        <Icon icon="mdi:account-circle-outline" width="24" />

        <Icon icon="line-md:moon-filled-loop" width="24" />
</nav> -->
            <nav>
                <button class="icon-btn">🔍</button>

                <ul class="nav-links">
                    <li><a href="#">Início</a></li>
                    <li><a href="#">Galeria</a></li>
                    <li><a href="#">Favoritos</a></li>
                </ul>

                <button class="icon-btn profile-btn">👤</button>

                <button @click="toggleDarkMode" class="theme-toggle">
                    {{ isDarkMode ? '☀️' : '🌙' }}
                </button>
            </nav>
        </div>
    </header>
</template>

<style scoped lang="scss">
header {
    border-bottom: 1px solid #eee;
    padding: 1.5rem 0;

    .header-container {
        max-width: 1200px;
        margin: 0 auto;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 2rem;
    }

    .logo {
        height: 45px;
    }

    nav {
        display: flex;
        align-items: center;
        gap: 30px;
    }

    .nav-links {
        display: flex;
        list-style: none;
        gap: 25px;

        a {
            text-decoration: none;
            color: var(--text-color);
            font-weight: 500;

            &:hover {
                color: var(--pink-primary);
            }
        }
    }

    .icon-btn {
        background: none;
        border: none;
        font-size: 1.2rem;
        cursor: pointer;
    }
}
</style>