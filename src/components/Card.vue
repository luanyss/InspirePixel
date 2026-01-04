<script setup>
import { ref } from 'vue';
// defineProps: Avisa ao Vue que este componente vai receber uma 'imagem' do pai (Inspire.vue)
defineProps(["imagem"]);

const liked = ref(false)
</script>

<template>
    <div class="card">
        <!-- ícone de favoritar -->
        <span class="heart" @click="liked = !liked">
            {{ liked ? "❤️" : "🤍" }}
        </span>
        <!-- operador ternario: uma forma mais simples de criar um if/else -->
        <!-- condição? se_o_valor_for_verdadeiro : valor_falso -->
        <img :src="imagem" alt="Imagem da Galeria">
    </div>
</template>

<style scoped lang="scss">
.card {
    position: relative;
    width: 260px; // Largura fixa aproximada do print
    height: 400px; // Altura maior para dar o efeito "retrato" do print
    overflow: hidden;
    border-radius: 12px;

    .heart {
        position: absolute;
        top: 15px;
        right: 15px;
        font-size: 1.4rem;
        z-index: 2;
        filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.3));
        cursor: pointer;
    }

    img {
        width: 100%;
        height: 100%;
        object-fit: cover; // Crucial para não deformar a foto
        transition: transform 0.3s ease;
    }

    &:hover img {
        transform: scale(1.05); // Efeito de zoom profissional ao passar o mouse
    }
}
</style>