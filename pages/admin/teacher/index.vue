<template lang="html">
    <div>
        <v-data-table :headers="headers" :items="desserts" item-key="teacher_id" class="elevation-1" :search="search">
            <template #top>
                <v-row>
                    <v-col cols="9">
                        <v-text-field v-model="search" label="Search" class="mx-4"></v-text-field>
                    </v-col>
                    <v-col class="pt-6">
                        <v-btn color="success" rounded class="me-2">Search</v-btn>
                        <v-btn color="primary" rounded to="./teacher/add_teacher"><v-icon dark>mdi-plus</v-icon>New
                            Teacher</v-btn>
                    </v-col>
                </v-row>
            </template>
            <template #[`item.actions`]="{ item }">
            <v-btn color="amber darken-3" :to="'./teacher/edit_teacher#' + item.teacher_id">
                <v-icon>
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
                    text: 'Teacher id',
                    align: 'start',
                    sortable: true,
                    value: 'teacher_id',
                },
                { text: 'First name', value: 'first_name' },
                { text: 'Last name', value: 'last_name' },
                { text: 'Actions', value: 'actions', sortable: false },
            ]
        },
    },
    created() {
        this.url = 'http://localhost/service_ip3/admin/teacher/show_teacher_name.php'
        axios.get(this.url).then((resp) => {
            // console.log(resp.data.response)
            this.desserts = resp.data.response
        })
    },
    methods: {
    },   
}
</script>
<style lang="css"></style>