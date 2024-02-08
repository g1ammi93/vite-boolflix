<script>
export default {
    name: 'ProductionCard',
    props: {
        item: Object
    },
    computed: {
        hasFlag() {
            const flags = ['it', 'en', 'pl'];
            return flags.includes(this.item.original_language);
        },
        flagSrc() {
            const url = new URL(`../assets/img/${this.item.original_language}.png`, import.meta.url);

            return url.href;
        }
    }
};
</script>

<template>
    <ul>
        <li>{{ item.title || item.name }} </li>
        <li>{{ item.original_title || item.original_name }}</li>
        <li>
            <img v-if="hasFlag" :src="flagSrc" :alt="item.original_language">
            <span v-else> {{ item.original_language }} </span>
        </li>
        <li>{{ Math.floor(item.vote_average) }} </li>
    </ul>
</template>

<style scoped >
img {
    max-width: 100px;
}
</style>