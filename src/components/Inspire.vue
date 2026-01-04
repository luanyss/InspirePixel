<script setup>
import { ref, onMounted } from 'vue'; //onMounted: Sem isso, a função de carregar imagens existia, mas nunca era chamada. Agora as fotos aparecem assim que o site abre.
import axios from 'axios';
import Card from './Card.vue';
//importando o axios -> é uma biblioteca JS para fazer requisições HTTP

//importamos o ref -> uma funcionalidade que permite criar variaveis reativas

//criar uma variavel reativa que vai receber a lista de imagens da api
const imagens = ref([]);

//função assíncrona -> 
// Função para buscar as fotos da API

const carregarImagens = async () => {
    try {
        // Busca 30 imagens para preencher bem a galeria
        const res = await axios.get("https://picsum.photos/v2/list?page=3&limit=30");
        imagens.value = res.data;
    } catch (error) {
        console.error("Erro ao buscar imagens:", error);
    }
};
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
    <section class="inspire-section">
        <h2>Inspire-se</h2>

        <div class="galeria-grid">
            <Card v-for="img in imagens" :key="img.id" :imagem="img.download_url" />
        </div>
    </section>
</template>

<style scoped lang="scss">
.inspire-section {
    max-width: 1200px;
    margin: 0 auto;
    padding: 2rem;

    h2 {
        font-size: 2rem;
        margin-bottom: 2rem;
        color: var(--text-color);
    }

    .galeria-grid {
        display: grid;
        // Cria colunas que se ajustam sozinhas: mínimo 250px, máximo 1 fração do espaço
        grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
        gap: 30px; // Espaço entre as fotos conforme o design
        justify-items: center;

        @media (max-width: 600px) {
            grid-template-columns: repeat(2, 1fr); // 2 colunas no celular 
            gap: 15px;
        }
    }
}
</style>