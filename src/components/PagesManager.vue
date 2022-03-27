<template>
    <button @click="onAddNewPage">Create</button>
    <br />
    <pages-displayer :pages="pages" />
    <NewPageFormPopup
        v-if="showNewPageFormPopup"
        @closePopup="onCloseNewPageFormPopup"
    />
</template>

<script>
import PagesDisplayer from "./PagesDisplayer.vue";
import NewPageFormPopup from "./NewPageFormPopup.vue";

export default {
    name: "PagesManager",
    components: {
        PagesDisplayer,
        NewPageFormPopup,
    },
    data() {
        return {
            showNewPageFormPopup: false,
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
        addNewPage(newPage) {
            if (newPage) {
                this.pages.unshift(newPage);
            }
        },
        onAddNewPage() {
            this.showNewPageFormPopup = true;
        },
        onCloseNewPageFormPopup(newPage) {
            this.showNewPageFormPopup = false;
            this.addNewPage(newPage);
        },
    },
};
</script>

<style>
</style>
