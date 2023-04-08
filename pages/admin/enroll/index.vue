<template lang="html">
    <div>
        <v-data-table :headers="headers" :items="desserts" item-key="student_id" class="elevation-1" :search="search">
            <template #top>
                <v-row>
                    <v-col cols="9">
                        <v-text-field v-model="search" label="Search" class="mx-4"></v-text-field>
                    </v-col>
                    <v-col class="pt-6">
                        <v-btn color="success" rounded class="me-2">Search</v-btn>
                        <v-btn color="primary" rounded to=""><v-icon dark>mdi-plus</v-icon>New
                            Class</v-btn>
                    </v-col>
                </v-row>
            </template>
            <template #[`item.actions`]="{ item }">
            <v-btn color="success" :to="'./enroll/edit_enroll?school_year=' + item.school_year +  '&grade=' + item.grade + '&room=' + item.room">
                <v-icon>
                    mdi-eye-outline
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
                    text: 'School year',
                    align: 'start',
                    sortable: true,
                    value: 'school_year',
                },
                { text: 'grade', value: 'grade' },
                { text: 'room', value: 'room' },
                { text: 'Actions', value: 'actions', sortable: false },
            ]
        },
    },
    created() {
        this.url = 'http://localhost/service_ip3/admin/enroll/show_classroom.php'
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