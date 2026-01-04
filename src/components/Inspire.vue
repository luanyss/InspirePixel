<script setup>
import { ref, onMounted } from 'vue'; //onMounted: Sem isso, a função de carregar imagens existia, mas nunca era chamada. Agora as fotos aparecem assim que o site abre.
import axios from 'axios';
import Card from './Card.vue';
//importando o axios -> é uma biblioteca JS para fazer requisições HTTP

//importamos o ref -> uma funcionalidade que permite criar variaveis reativas

//criar uma variavel reativa que vai receber a lista de imagens da api
const imagens = ref([]);

//função assíncrona -> 
async function carregarImagens() {
    try {
        const res = await axios.get("https://picsum.photos/v2/list?page=3&limit=30");
        imagens.value = res.data;
    } catch (error) {
        console.error("Erro ao carregar imagens:", error);
    }
}
//res -> resposta da API
//AXIOS pegar os dados GET axios.get()
//await você precisa esperar o axios buscar as imagens
//guardando as imagens da API dentro da variavel imagens
// Isso faz as imagens carregarem sozinhas quando abre o site!
onMounted(() => {

    carregarImagens();
});
</script>


<template>
    <main>
        <h2>Inspire-se</h2>
        <section class="inspire-container">
            <Card v-for="img in imagens" :key="img.id" :imagem="img.download_url" />
        </section>
    </main>
</template>

<style scoped lang="scss">
h2 {
    margin: 2rem;
}

.inspire-container {
    display: flex;
    flex-wrap: wrap; // Para os cards caírem para a linha de baixo
    justify-content: center;
    gap: 20px;
    padding: 1rem;
}
</style>