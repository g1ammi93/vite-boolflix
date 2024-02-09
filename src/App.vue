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
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    background-color: black;
}

.container {
    max-width: 1428px;
    margin: 0 auto;

}

.fas {
    color: rgb(229, 207, 75);
    cursor: pointer;
}

.far:hover {
    color: rgb(229, 207, 75);
    cursor: pointer;
}

ul {
    list-style: none;
}
</style>
