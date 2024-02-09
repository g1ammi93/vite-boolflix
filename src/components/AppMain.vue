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
        <div class="container">
            <section id="section-movie">
                <h2>Movies</h2>
                <div class="flex">
                    <ProductionCard v-for="movie in store.movies" :key="movie.id" :item="movie" />
                </div>
            </section>
            <section id="section-series">
                <h2>Tv Series</h2>
                <div class="flex">
                    <ProductionCard v-for="serie in store.series" :key="serie.id" :item="serie" />
                </div>
            </section>
        </div>
    </main>
</template>

<style scoped>
h2 {
    padding-top: 20px;
    margin: 20px 0;
    font-size: 40px;
    color: black;
}

main {
    background-color: darkgray;
}

.flex {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
}
</style>