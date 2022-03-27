<template>
    <div class="popup">
        <div class="popup-inner">
            <form role="form" @submit="onSubmit">
                <div class="form-group">
                    <label for="url">URL</label>
                    <input
                        id="url"
                        type="text"
                        v-model.trim="url"
                        autocomplete="none"
                        placeholder="Please Enter a vaild URL"
                        class="form-control"
                    />
                </div>

                <div class="col-sm-10">
                    <label for="locale">Locale</label>
                    <select
                        id="locale"
                        name="locale"
                        v-model="locale"
                        class="form-control m-b"
                    >
                        <option
                            v-for="locale in localeOptions"
                            :key="locale.value"
                        >
                            {{ locale.display }}
                        </option>
                    </select>
                </div>

                <div class="col-sm-10">
                    <label for="template">Template</label>
                    <select
                        id="template"
                        name="template"
                        v-model="template"
                        class="form-control m-b"
                    >
                        <option
                            v-for="template in templateOptions"
                            :key="template.value"
                        >
                            {{ template.display }}
                        </option>
                    </select>
                </div>
                <div>
                    <button
                        class="btn btn-sm btn-primary m-t-n-xs"
                        type="button"
                        @click="onCancel"
                    >
                        <strong>cancel</strong>
                    </button>
                    <button
                        class="btn btn-sm btn-primary m-t-n-xs"
                        type="submit"
                        @click="onSubmit"
                    >
                        <strong>Create</strong>
                    </button>
                </div>
            </form>
        </div>
    </div>
</template>

<script>
export default {
    emits: ["closePopup"],
    data: function () {
        return {
            url: "",
            localeOptions: [
                { display: "FR", value: "fr" },
                { display: "EN", value: "en" },
            ],
            locale: "",
            templateOptions: [
                { display: "Blog", value: "blog" },
                { display: "Another Blog", value: "blog" },
            ],
            template: "",
        };
    },
    methods: {
        onCancel() {
            this.$emit("closePopup");
        },

        onSubmit() {
            if (!this.url || !this.locale || !this.template) {
                this.$emit("closePopup");
            }

            this.$emit("closePopup", {
                url: this.url,
                createdAt: Date.now(),
                locale: this.locale,
                template: this.template,
            });
        },
    },
};
</script>

<style lang="scss" scoped>
.popup {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 100;
    background-color: rgba(0, 0, 0, 0.2);

    display: flex;
    align-items: center;
    justify-content: center;

    .popup-inner {
        background-color: #fff;
        padding: 20px;
        border-radius: 5px;
        max-width: 500px;
        max-height: 500px;
        overflow: auto;
        display: flex;
        flex-direction: column;
        align-items: center;
    }
}
</style>