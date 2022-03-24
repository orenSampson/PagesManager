<template>
    <div>Pages Component</div>
    <ul>
        <li v-for="page in pages" :key="page.url">{{ page.url }}</li>
    </ul>
</template>

<script>
export default {
    name: "PagesDisplayer",
    props: {
        pages: {
            type: Array,
            required: true,
        },
    },
};
</script>

<style>
</style>