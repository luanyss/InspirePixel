<script setup>
// 1. Importamos as imagens da pasta assets
// Certifique-se de que os nomes dos arquivos na pasta sejam exatamente esses
// Importamos as imagens com CONST (porque o caminho do arquivo não muda)
import logo from "../assets/logo.png"
import iconeBusca from "../assets/lupa.svg"
import iconePerfil from "../assets/perfil.svg"
import { ref } from 'vue'

// 2. Lógica para o Dark Mode usando CONST e REATIVIDADE
const isDarkMode = ref(false)

const toggleDarkMode = () => {
    isDarkMode.value = !isDarkMode.value
    // Isso coloca ou tira a classe "dark-mode" do corpo da página
    // Pegamos a lista de classes do body com uma CONST
    const bodyClass = document.body.classList
    bodyClass.toggle('dark-mode')
}
</script>

<template>
    <header>
        <div class="header-container">
            <img :src="logo" alt="Logo Inspire Pixel" class="logo">

            <nav>
                <ul>
                    <li>
                        <button class="icon-btn search-wrapper">
                            <img :src="iconeBusca" alt="Buscar" class="lupa-icon">
                        </button>
                    </li>

                    <li><a href="#">Início</a></li>
                    <li><a href="#">Galeria</a></li>
                    <li><a href="#">Favoritos</a></li>

                    <li>
                        <button class="icon-btn">
                            <img :src="iconePerfil" alt="Perfil">
                        </button>
                    </li>

                    <li>
                        <button @click="toggleDarkMode" class="theme-btn">
                            {{ isDarkMode ? '☀️' : '🌙' }}
                        </button>
                    </li>
                </ul>
            </nav>
        </div>
    </header>
</template>

<style scoped lang="scss">
header {
    /* Aqui no CSS, o 'var()' é obrigatório para ler as variáveis do global.scss */
    border-bottom: 1px solid #eee;
    padding: 1rem 0;
    background-color: var(--bg-color); // Usa a variável que criamos no global.scss

    .header-container {
        max-width: 1200px;
        margin: 0 auto;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 2rem;
    }

    .logo {
        height: 40px; // Ajuste conforme o tamanho da sua logo
    }

    nav ul {
        display: flex;
        align-items: center;
        list-style: none;
        gap: 20px;

        li a {
            text-decoration: none;
            color: var(--text-color);
            font-weight: 500;
            font-size: 0.9rem;

            &:hover {
                color: #E1306C; // Rosa do design
            }
        }
    }

    .lupa-icon {
        width: 22px;
        height: 22px;
        transition: filter 0.3s ease, transform 0.3s ease;

        /* Quando o body tiver a classe dark-mode, a lupa brilha */
        :deep(body.dark-mode) & {
            filter: invert(1) brightness(2); // Torna o ícone branco e brilhante
        }

        &:hover {
            transform: scale(1.1);
            filter: drop-shadow(0 0 5px #E1306C); // Brilho rosa ao passar o mouse
        }
    }

    // Juntei as repetições em um bloco só aqui:
    .icon-btn,
    .theme-btn {
        background: none;
        border: none;
        cursor: pointer;
        display: flex;
        align-items: center;

        img {
            width: 22px;
            height: 22px;
        }
    }

    .theme-btn {
        font-size: 1.2rem;
        margin-left: 10px;
    }
}

// Responsividade
@media (max-width: 768px) {
    nav ul li a {
        display: none; // Esconde os textos Início/Galeria no celular para não amassar
    }
}
</style>