<template>
    <div class="page container">
        <h1 class="pages-header">All Pages</h1>
        <span class="page-button">
            <button @click="onAddNewPage">+</button>
        </span>
        <pages-displayer :pages="pages" />
        <new-page-form-popup
            v-if="showNewPageFormPopup"
            @closePopup="onCloseNewPageFormPopup"
        />
    </div>
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

<style lang="scss" scoped>
.page {
    display: flex;
    flex-direction: column;
}
.pages-header {
    text-align: center;
}
.page-button {
    display: flex;
    justify-content: flex-end;
    margin-bottom: 1rem;
}
</style>
