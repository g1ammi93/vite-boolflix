<script>
import axios from 'axios'
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
                return;
            }

            const { baseUri, language, apiKey } = api;

            const apiConfg = {
                params: {
                    query: this.titleFilter,
                    api_key: apiKey,
                    language
                }
            }
            axios.get(`${baseUri}/search/movie`, apiConfg)
                .then((res) => {
                    store.movie = res.data.results;
                })

                .catch((err) => {
                    console.error(err)
                })
        }
    }

};
</script>

<template>
    <SearchBar @form-submit="searchProduct" @term-change="setTitleFilter" placeholder="Cerca..." buttonLabel="Cerca" />
</template>

<style ></style>