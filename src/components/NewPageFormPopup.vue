<template>
    <div class="popup">
        <div v-click-outside="onCancel">
            <div class="popup-inner jumbotron jumbotron-style">
                <div class="row">
                    <div class="col-2"></div>
                    <h3 class="col-8 text-center"><u>Add A New Page</u></h3>
                    <div class="col-1"></div>
                    <button
                        class="btn btn-sm btn-success col-1 text-center"
                        type="button"
                        @click="onCancel"
                    >
                        <strong>X</strong>
                    </button>
                </div>

                <form role="form" @submit.prevent="onSubmit">
                    <div
                        class="form-group"
                        :class="{ urlInvalid: !!this.urlErrorMessage }"
                    >
                        <label for="url">URL</label>
                        <input
                            id="url"
                            type="text"
                            v-model.trim="url"
                            @blur="checkIfURLValid"
                            autocomplete="none"
                            placeholder="Please Enter a vaild URL"
                            class="form-control"
                        />
                        <p v-if="this.urlErrorMessage">
                            * {{ this.urlErrorMessage }}
                        </p>
                    </div>

                    <div>
                        <label for="locale">Locale</label>
                        <select
                            id="locale"
                            name="locale"
                            v-model="locale"
                            class="form-control m-b"
                        >
                            <option
                                v-for="locale in localeOptions"
                                :key="locale"
                            >
                                {{ locale }}
                            </option>
                        </select>
                    </div>

                    <div>
                        <label for="template">Template</label>
                        <select
                            id="template"
                            name="template"
                            v-model="template"
                            class="form-control m-b"
                        >
                            <option
                                v-for="template in templateOptions"
                                :key="template"
                            >
                                {{ template }}
                            </option>
                        </select>
                    </div>
                    <div class="d-flex justify-content-center">
                        <button
                            class="btn btn-success"
                            type="submit"
                            @click="onSubmit"
                            :disabled="isSubmitBtnIsDisabled"
                        >
                            <strong>Create</strong>
                        </button>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
import { LOCALE_OPTIONS, TEMPLATE_OPTIONS } from "../constants/formValues";

export default {
    emits: ["closePopup"],
    data: function () {
        return {
            url: "",
            urlErrorMessage: "",
            localeOptions: LOCALE_OPTIONS,
            locale: LOCALE_OPTIONS?.length ? LOCALE_OPTIONS[0] : "",
            templateOptions: TEMPLATE_OPTIONS,
            template: TEMPLATE_OPTIONS?.length ? TEMPLATE_OPTIONS[0] : "",

            vcoConfig: {
                //data for click-outside-vue3 library
                handler: this.handler,
                middleware: this.middleware,
                events: ["dblclick", "click"],
                // Note: The default value is true, but in case you want to activate / deactivate
                //       this directive dynamically use this attribute.
                isActive: true,
                // Note: The default value is true. See "Detecting Iframe Clicks" section
                //       to understand why this behaviour is behind a flag.
                detectIFrame: true,
                // Note: The default value is false. Sets the capture option for EventTarget addEventListener method.
                //       Could be useful if some event's handler calls stopPropagation method preventing event bubbling.
                capture: false,
            },
        };
    },
    methods: {
        onCancel() {
            this.$emit("closePopup");
        },

        checkIfURLValid() {
            console.log("checkURLValidity called");
            if (!this.url) {
                this.urlErrorMessage = "URL is required";
                return false;
            } else {
                this.urlErrorMessage = "";
                return true;
            }
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
    computed: {
        isSubmitBtnIsDisabled() {
            return !this.url || !this.locale || !this.template;
        },
    },
};
</script>

<style lang="scss" scoped>
label {
    font-weight: bold;
}

button:disabled {
    cursor: not-allowed;
    pointer-events: all !important;
}

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
        width: 26rem;
        background-color: #fff;
    }
}

.urlInvalid {
    label {
        color: red;
    }
    input {
        border-color: red;
    }
}

.jumbotron-style {
    padding-top: 1rem;
    padding-bottom: 1rem;
}
</style>