<template>
    <pages-displayer :pages="pages" />
    <br />
    <button @click="onAddNewPage">Create New Page</button>
    <page-popup :display="showAddNewPagePopup">
        <h2>My Popup Content</h2>
    </page-popup>
</template>

<script>
import PagesDisplayer from "./PagesDisplayer.vue";
import PagePopup from "./PagePopup.vue";

export default {
    name: "PagesManager",
    components: {
        PagesDisplayer,
        PagePopup,
    },
    data() {
        return {
            showAddNewPagePopup: false,
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
        onAddNewPage() {
            this.showAddNewPagePopup = !this.showAddNewPagePopup;
        },
    },
};
</script>

<style>
</style>
