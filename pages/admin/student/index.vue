<template lang="html">
    <div>
        <v-data-table :headers="headers" :items="desserts" item-key="student_id" class="elevation-1" :search="search"
            :custom-filter="filterOnlyCapsText">
            <template v-slot:top>
                <v-row>
                    <v-col cols="9">
                        <v-text-field v-model="search" label="Search (UPPER CASE ONLY)" class="mx-4"></v-text-field>
                    </v-col>
                    <v-col class="pt-6">
                        <v-btn color="success" rounded class="me-2">Search</v-btn>
                        <v-btn color="primary" rounded to="./student/add_student"><v-icon dark>mdi-plus</v-icon>New
                            Student</v-btn>
                    </v-col>
                </v-row>
            </template>
            <template v-slot:item.actions="{ item }">
            <v-btn color="success" :to="item.student_id">
                <v-icon small class="mr-2">
                    mdi-pencil
                </v-icon>
            </v-btn>
        </template>
        </v-data-table>
    </div>
</template>
<script>
import axios from 'axios';
export default {
    layout: 'admin',
    data() {
        return {
            search: '',
            calories: '',
            desserts: []
        }
    },
    computed: {
        headers() {
            return [
                {
                    text: 'Student id',
                    align: 'start',
                    sortable: true,
                    value: 'student_id',
                },
                { text: 'First name', value: 'fist_name' },
                { text: 'Last name', value: 'last_name' },
                { text: 'Actions', value: 'actions', sortable: false },
            ]
        },
    },
    methods: {
        filterOnlyCapsText(value, search, item) {
            return value != null &&
                search != null &&
                typeof value === 'string' &&
                value.toString().toLocaleUpperCase().indexOf(search) !== -1
        },
    },
    created() {
        this.url = 'http://localhost/service/admin/show_student_name.php'
        axios.get(this.url).then((resp) => {
            console.log(resp.data.response)
            this.desserts = resp.data.response
        })
    }
}
</script>
<style lang="css"></style>