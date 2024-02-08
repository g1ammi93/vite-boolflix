<script>
import { store } from '../data/store';
export default {
    name: 'MainBoolfix',
    data: () => ({ store })

};
</script>

<template>
    <main>
        <h2>Movie</h2>
        <ul v-for="movie in store.movies" :key="movie.id">
            <li>{{ movie.title }}</li>
            <li>{{ movie.original_title }}</li>
            <li>{{ movie.original_language }}</li>
            <li>{{ Math.floor(movie.vote_average) }}</li>
        </ul>
    </main>
</template>

<style ></style>