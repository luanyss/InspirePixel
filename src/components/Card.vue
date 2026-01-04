<script setup>
import { ref } from 'vue';
import iconeCoracao from "../assets/coracao.svg"
// defineProps: Avisa ao Vue que este componente vai receber uma 'imagem' do pai (Inspire.vue)
defineProps(["imagem"]);

const liked = ref(false)
</script>

<template>
    <div class="card">
        <img 
            :src="iconeCoracao" 
            class="heart-icon" 
            :class="{ 'is-liked': liked }" 
            @click="liked = !liked"
            alt="Favoritar"
        >
        <img :src="imagem" alt="Imagem da Galeria" class="main-img">
    </div>
</template>

<style scoped lang="scss">
.card {
    position: relative;
    width: 100%;
    height: 400px;
    border-radius: 15px;
    overflow: hidden;
    cursor: pointer;

    .heart-icon {
        position: absolute;
        top: 15px;
        right: 15px;
        width: 26px;
        z-index: 10;
        transition: all 0.3s ease;
        
        // 1. Estado Normal: Fica Branco
        filter: brightness(0) invert(1); 
        opacity: 0.8;

        &.is-liked {
            opacity: 1;
            transform: scale(1.2);
            
            // 2. Estado Ativo: Filtro que transforma o ícone em ROSA (#E1306C)
            // Esse filtro calcula a rotação de cores para chegar no rosa exato
            filter: invert(27%) sepia(91%) saturate(2352%) hue-rotate(323deg) brightness(91%) contrast(93%) !important;
        }

        &:hover {
            transform: scale(1.1);
        }
    }

    .main-img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        transition: transform 0.5s ease;
    }

    &:hover .main-img {
        transform: scale(1.05);
    }
}
</style>