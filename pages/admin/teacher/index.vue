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
                        <v-btn color="primary" rounded to="./teacher/add_teacher"><v-icon dark>mdi-plus</v-icon>New
                            Teacher</v-btn>
                    </v-col>
                </v-row>
            </template>
            <template v-slot:item.actions="{ item }">
            <v-btn color="success" :to="item.teacher" to="./teacher/edit_teacher">
                <v-icon>
                    mdi-pencil
                </v-icon>
            </v-btn>
            <v-btn color="red" :to="item.teacher_id">
                <v-icon>
                    mdi-delete
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
            desserts: [
                {   teacher_id:'T15255',
                    frist_name:'Somsak',
                    last_name:'Srisuk'
                },
                {   teacher_id:'T15256',
                    frist_name:'Thana',
                    last_name:'nan'
                },
            ],
        }
    },
    computed: {
        headers() {
            return [
                {
                    text: 'Teacher id',
                    align: 'start',
                    sortable: true,
                    value: 'teacher_id',
                },
                { text: 'First name', value: 'frist_name' },
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
        this.url = 'http://localhost/service/admin/show_teacher_name.php'
        axios.get(this.url).then((resp) => {
            console.log(resp.data.response)
            this.desserts = resp.data.response
        })
    }
}
</script>
<style lang="css"></style>