<script>
export default {
    name: 'SearchBar',
    data: () => ({ term: '' }),
    props: {
        buttonLabel: String,
        placeholder: String
    },
    emits: ['form-submit', 'term-change']
};
</script>

<template>
    <form @submit.prevent="$emit('form-submit', term)">
        <input type="text" v-model.trim="term" :placeholder="placeholder" @keyup="$emit('term-change', term)">
        <button>{{ buttonLabel }}</button>
    </form>
</template>

<style ></style>