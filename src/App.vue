<template>
    <span class="container">
        <h1 class="text-center">All Pages</h1>
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
    background-color: white;
}
</style>
