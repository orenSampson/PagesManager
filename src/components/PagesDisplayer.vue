<template>
    <div>
        <table
            class="
                table table-striped table-bordered table-hover
                dataTables-example
                dataTable
            "
            id="DataTables_Table_0"
            aria-describedby="DataTables_Table_0_info"
            role="grid"
        >
            <thead>
                <tr role="row">
                    <th
                        class="sorting_asc"
                        tabindex="0"
                        aria-controls="DataTables_Table_0"
                        rowspan="1"
                        colspan="1"
                        aria-sort="ascending"
                        aria-label="Rendering engine: activate to sort column descending"
                        style="width: 289.188px"
                    >
                        Pages
                    </th>
                    <th
                        class="sorting"
                        tabindex="0"
                        aria-controls="DataTables_Table_0"
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
                <tr v-for="page in pages" :key="page.url" role="row">
                    <td>{{ page.url }}</td>
                    <td>
                        {{
                            this.formatMethod(
                                page.createdAt,
                                "yyyy-MM-dd HH:mm:ss"
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
    },
};
</script>

<style>
</style>