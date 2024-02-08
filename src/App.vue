<script>
import { store } from './data/store';
import { api } from './data/index';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
export default {
    name: 'Boolflix',
    components: { AppHeader, AppMain }
};
</script>

<template>
    <AppHeader />
    <AppMain />
</template>

<style ></style>
