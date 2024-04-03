<template>
    <article class="cards-wrapper">
        <Card v-for="n in 3" :key="n" :hasAnimation="n === 2"/>
    </article>
</template>
<script setup>
import Card from './Card.vue'
</script>
<style scoped>
    .cards-wrapper {
        display: flex;
        gap: 16px
    }
</style>
