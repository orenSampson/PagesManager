<template>
    <div class="page">
        <span class="page-button">
            <button
                @click="onAddNewPage"
                type="button"
                class="btn btn-w btn-success"
            >
                +
            </button>
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
import { PAGES } from "../constants/formValues";

export default {
    name: "PagesManager",
    mounted() {
        if (localStorage.getItem("pages")) {
            this.pages = JSON.parse(localStorage.getItem("pages"));

            if (!this.pages?.length) {
                this.pages = [];
            }
        } else {
            localStorage.setItem("pages", JSON.stringify(PAGES));
            this.pages = PAGES;
        }
    },
    components: {
        PagesDisplayer,
        NewPageFormPopup,
    },
    data() {
        return {
            showNewPageFormPopup: false,
            pages: [],
        };
    },
    methods: {
        addNewPage(newPage) {
            if (newPage) {
                this.pages.unshift(newPage);
                localStorage.setItem("pages", JSON.stringify(this.pages));
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

.page-button {
    display: flex;
    justify-content: flex-end;
    margin-bottom: 1rem;
}
</style>
