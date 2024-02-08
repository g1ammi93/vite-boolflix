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

<style >
.fas {
    color: rgb(229, 207, 75);
    cursor: pointer;
}

.far:hover {
    color: rgb(229, 207, 75);
    cursor: pointer;
}
</style>
