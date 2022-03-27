<template>
    <span class="container">
        <h1 class="pages-header">All Pages</h1>
        <pages-manager />
    </span>
</template>

<script>
import PagesManager from "./components/PagesManager.vue";

export default {
    name: "App",
    components: {
        PagesManager,
    },
};
</script>

<style lang="scss">
body {
    background-color: white !important;
}
.pages-header {
    text-align: center;
}
</style>
