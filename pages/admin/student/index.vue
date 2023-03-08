<template lang="html">
    <div>
        <v-data-table :headers="headers" :items="desserts" item-key="student_id" class="elevation-1" :search="search"
            :custom-filter="filterOnlyCapsText">
            <template v-slot:top>
                <v-row>
                    <v-col cols="6">
                        <v-select :items="classs" label="Class" dense class="mx-4"></v-select>
                    </v-col>
                    <v-col cols="6">
                        <v-select :items="rooms" label="Room" dense class="mx-4"></v-select>
                    </v-col>
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
            <v-btn color="success" :to="item.student_id" to="./student/edit_student">
                <v-icon>
                    mdi-pencil
                </v-icon>
            </v-btn>
            <v-btn color="red" :to="item.student_id">
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
                {   student_id:'S15523',
                    fist_name:'Somsak',
                    last_name:'Srisuk'
                }
            ],
            classs: ['1', '2', '3', '4','5','6'],
            rooms: ['1', '2']
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