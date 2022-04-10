<template>
    <div class="animated fadeInRight">
        <table
            class="
                table table-striped table-bordered table-hover
                dataTables-example
                dataTable
            "
            id="all_pages_dataTables"
            aria-describedby="all_pages_dataTables"
            role="grid"
        >
            <thead>
                <tr role="row">
                    <th
                        class="sorting_asc"
                        tabindex="0"
                        aria-controls="all_pages_dataTables"
                        rowspan="1"
                        colspan="1"
                        aria-sort="ascending"
                        aria-label="Rendering Pages: activate to sort column descending"
                        style="width: 289.188px"
                    >
                        Pages
                    </th>
                    <th
                        class="sorting_asc"
                        tabindex="0"
                        aria-controls="all_pages_dataTables"
                        rowspan="1"
                        colspan="1"
                        aria-sort="ascending"
                        aria-label="Rendering Template: activate to sort column descending"
                        style="width: 289.188px"
                    >
                        Template
                    </th>
                    <th
                        class="sorting_asc"
                        tabindex="0"
                        aria-controls="all_pages_dataTables"
                        rowspan="1"
                        colspan="1"
                        aria-label="Browser: activate to sort column ascending"
                        style="width: 356.016px"
                    >
                        Created At
                    </th>
                </tr>
            </thead>

            <tbody>
                <tr
                    v-for="(page, index) in pages"
                    :key="page.url"
                    role="row"
                    class="gradeA"
                    :class="{ even: index % 2 !== 0, odd: index % 2 === 0 }"
                >
                    <td class="sorting_1">
                        <a :href="urlToEditor(page.url)" target="_blank">{{
                            page.url
                        }}</a>
                    </td>
                    <td class="sorting_1">
                        {{ page.template }}
                    </td>
                    <td class="sorting_1">
                        {{
                            this.formatMethod(
                                page.createdAt,
                                formatterByLocale(page.locale)
                            )
                        }}
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import { format } from "date-fns";

export default {
    name: "PagesDisplayer",
    props: {
        pages: {
            type: Array,
            required: true,
        },
    },
    methods: {
        formatMethod(date, formatString) {
            return format(date, formatString);
        },
        formatterByLocale(locale) {
            switch (locale) {
                case "FR":
                    return "yyyy-MM-dd HH:mm:ss";

                case "EN":
                    return "yyyy-MM-dd HH:mm:ss";

                default:
                    return "yyyy-MM-dd HH:mm:ss";
            }
        },
        urlToEditor(url) {
            return `${url}?mode=edit`;
        },
    },
};
</script>

<style>
</style>