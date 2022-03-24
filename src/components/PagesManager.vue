<template>
    <pages-displayer :pages="pages" />
    <br />
    <button>Hi</button>
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
                    createdAt: Date.now(),
                    locale: "FR",
                    template: "blog",
                },
                {
                    url: "cd",
                    createdAt: Date.now(),
                    locale: "FR",
                    template: "blog",
                },
                {
                    url: "ef",
                    createdAt: Date.now(),
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
