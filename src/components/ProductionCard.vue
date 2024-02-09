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
        starVote(vote) {
            const fiveVote = Math.floor(Math.round(vote / 2));
            const starFull = '<i class="fas fa-star"></i>';
            const starEmpty = '<i class="far fa-star"></i>';

            return starFull.repeat(fiveVote) + starEmpty.repeat(5 - fiveVote);

        },
        starPage(vote) {
            return 'Voto:' + this.starVote(vote);
        }
    }
};
</script>

<template>
    <ul>
        <li class="cover-container">
            <img :src="item.backdrop_path ? `${coverUri}${dimensionUri}/${item.backdrop_path}` : 'https://www.altavod.com/assets/images/poster-placeholder.png'"
                alt="" class="cover">
            <ul class="overlay">

                <li><span>Titolo:</span> {{ item.title || item.name }} </li>
                <li><span>Titolo originale:</span>{{ item.original_title || item.original_name }}</li>
                <li>
                    <span>Lingua:</span>
                    <img v-if="hasFlag" :src="flagSrc" :alt="lang" class="flag">
                    <span v-else> {{ lang }} </span>
                </li>
                <li v-html="starPage(item.vote_average)"></li>
            </ul>
        </li>
    </ul>
</template>

<style scoped >
.flag {
    max-width: 80px;
}

.cover {
    width: 342px;
    height: 500px;
    object-fit: cover;
    cursor: pointer;
}

span {
    font-weight: bold;
}

.overlay {
    position: absolute;
    top: 0;
    left: 0;
    display: flex;
    flex-direction: column;
}

.cover-container {
    position: relative;
}
</style>