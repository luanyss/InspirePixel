<script setup>
import Card from './Card.vue';

</script>

<template>
    <h2>Inspire-se</h2>
    <section class="inspire">
        <Card imagem="" />
        <Card imagem="" />
        <Card imagem="" />
    </section>


</template>

<style scoped lang="scss">
.inspire h2{
    display: flex;
    justify-content: space-between;
    gap: 10px;
    margin: 2rem;
}
</style>