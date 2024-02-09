<script>
import axios from 'axios';
import { store } from '../data/store';
import { api } from '../data/index';
import SearchBar from './SearchBar.vue';
export default {
    name: 'HeaderBoolflix',
    data: () => ({ store, titleFilter: '' }),
    components: { SearchBar },
    methods: {
        setTitleFilter(term) {
            this.titleFilter = term;
        },
        searchProduct() {
            if (!this.titleFilter) {
                store.movies = [];
                store.series = [];
                return;
            }

            this.fetchApi('search/movie', 'movies');
            this.fetchApi('search/tv', 'series');
        },

        fetchApi(endpoint, collection) {

            const { baseUri, language, apiKey } = api;

            const apiConfg = {
                params: {
                    query: this.titleFilter,
                    api_key: apiKey,
                    language
                }
            }
            axios.get(`${baseUri}/${endpoint}`, apiConfg)
                .then((res) => {
                    store[collection] = res.data.results;
                })

                .catch((err) => {
                    console.error(err)
                })
        }
    }

};
</script>

<template>
    <header class="container">
        <div>
            <h1>BOOLFLIX</h1>
        </div>
        <div>
            <SearchBar @form-submit="searchProduct" @term-change="setTitleFilter" placeholder="Cerca..."
                buttonLabel="Cerca" />
        </div>
    </header>
</template>

<style scoped>
h1 {
    color: red;
}

.container {
    max-width: 1428px;
    margin: 0 auto;
}

header {
    height: 100px;
    background-color: black;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
</style>