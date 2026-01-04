<script setup>
// 1. Importando a imagem com o nome e extensão corretos
import fotografo from "../assets/fotografo.png"
</script>

<template>
    <section class="banner">
        <div class="banner-content">
            <div class="text-side">
                <h1>Onde a paisagem vira <span>inspiração.</span></h1>
                <p>Explore paisagens, cores e luzes que inspiram novas histórias através da fotografia.</p>
            </div>

            <div class="image-side">
                <img :src="fotografo" alt="Pessoa fotografando" class="img-fotografo">
            </div>
        </div>
    </section>
</template>

<style scoped lang="scss">
.banner {
    padding: 4rem 2rem;
    max-width: 1200px;
    margin: 0 auto;

    .banner-content {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 40px;

        // Ajuste para celular: o texto fica em cima e a imagem embaixo
        @media (max-width: 768px) {
            flex-direction: column;
            text-align: center;
        }
    }

    .text-side {
        flex: 1;

        h1 {
            font-size: 3.5rem;
            line-height: 1.1;
            font-weight: 800;
            color: var(--text-color);

            span {
                color: #E1306C; // O rosa do design
                display: block; // Faz a palavra "inspiração" cair para a linha de baixo
            }

            @media (max-width: 480px) {
                font-size: 2.5rem;
            }
        }

        p {
            margin-top: 1.5rem;
            font-size: 1.1rem;
            color: #666;
            max-width: 400px;

            @media (max-width: 768px) {
                margin: 1.5rem auto 0;
            }
        }
    }

    .image-side {
        flex: 1;
        display: flex;
        justify-content: flex-end;

        @media (max-width: 768px) {
            justify-content: center;
            width: 100%;
        }

        .img-fotografo {
            width: 100%;
            max-width: 450px; // Tamanho aproximado do Figma
            border-radius: 80px 20px 80px 20px; // Aquele arredondado estiloso do design
            object-fit: cover;
        }
    }
}
</style>