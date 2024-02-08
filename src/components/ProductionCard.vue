<script>
import { store } from '../data/store'
import axios from 'axios';
export default {
    name: 'ProductionCard',
    data() {
        return {
            coverUri: 'https://image.tmdb.org/t/p',
            dimensionUri: '/w342'
        }
    },
    props: {
        item: Object
    },
    computed: {
        hasFlag() {
            const flags = ['it', 'en', 'pl'];
            return flags.includes(this.lang);
        },
        lang() {
            return this.item.original_language;
        },
        flagSrc() {
            const url = new URL(`../assets/img/${this.lang}.png`, import.meta.url);

            return url.href;
        }
    },
    methods: {
        StarVote(vote) {
            return Math.floor(Math.round(vote / 2));
        }
    }
};
</script>

<template>
    <ul>
        <li> <img :src="`${coverUri}${dimensionUri}/${item.backdrop_path}`" alt=""> </li>
        <li>{{ item.title || item.name }} </li>
        <li>{{ item.original_title || item.original_name }}</li>
        <li>
            <img v-if="hasFlag" :src="flagSrc" :alt="lang" class="flag">
            <span v-else> {{ lang }} </span>
        </li>
        <li>{{ StarVote(item.vote_average) }} <i class="fa-regular fa-star"></i><i class="fa-regular fa-star"><i
                    class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i></i>
        </li>
    </ul>
</template>

<style scoped >
.flag {
    max-width: 80px;
}
</style>