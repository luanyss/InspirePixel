<script setup>
defineProps(["imagem"]);
//o que é define props
//
</script>

<template>

    <div>
        <img src="imagem" alt="Imagem do card">
    </div>
</template>

<style scoped lang="scss">
.card{
    border: solid;
    width: 35vw;

    img{
        width: 100%;
        height: 100%;
        border-radius: 10px;
    }
}
</style>