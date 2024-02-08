<script>
import { store } from '../data/store';
import ProductionCard from './ProductionCard.vue';
export default {
    name: 'MainBoolfix',
    data: () => ({ store }),
    components: { ProductionCard }
};
</script>

<template>
    <main>
        <section id="section-movie">
            <h2>Movie</h2>
            <ProductionCard v-for="movie in store.movies" :key="movie.id" :item="movie" />
        </section>
        <section id="section-series">
            <h2>Tv Series</h2>
            <ProductionCard v-for="serie in store.series" :key="serie.id" :item="serie" />
        </section>
    </main>
</template>

<style ></style>