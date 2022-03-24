<template>
    <div>PagesManager Component</div>
    <pages-displayer :pages="pages" />
    <button @click="addPage">Add Page</button>
</template>

<script>
import PagesDisplayer from "./PagesDisplayer.vue";

export default {
    name: "PagesManager",
    components: {
        PagesDisplayer,
    },
    data() {
        return {
            pages: [
                {
                    url: "ab",
                    locale: "FR",
                    template: "blog",
                },
                {
                    url: "cd",
                    locale: "FR",
                    template: "blog",
                },
                {
                    url: "ef",
                    locale: "FR",
                    template: "blog",
                },
            ],
        };
    },
    methods: {
        addPage() {
            this.pages.push({
                url: "",
                locale: "FR",
                template: "blog",
            });
        },
    },
};
</script>

<style>
</style>
