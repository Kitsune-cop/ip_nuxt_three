<template lang="html">
    <div>
        <v-data-table :headers="headers" :items="desserts" item-key="subject_id" class="elevation-1" :search="search">
            <template #top>
                <v-row>
                    <v-col cols="9">
                        <v-text-field v-model="search" label="Search" class="mx-4"></v-text-field>
                    </v-col>
                    <v-col class="pt-6">
                        <v-btn color="success" rounded class="me-2">Search</v-btn>
                        <v-btn color="primary" rounded to="./subject/add_subject"><v-icon dark>mdi-plus</v-icon>New
                            Subject</v-btn>
                    </v-col>
                </v-row>
            </template>
            <template #[`item.actions`]="{ item }">
            <v-btn color="amber darken-3" :to="'./advicers/edit_advicers?school_year=' + item.school_year +  '&grade=' + item.grade + '&room=' + item.room">
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
                    text: 'Grade',
                    align: 'start',
                    sortable: true,
                    value: 'grade',
                },
                { text: 'Room', value: 'room' },
                { text: 'Actions', value: 'actions', sortable: false },
            ]
        },
    },
    created() {
        this.url = 'http://localhost/service_ip3/admin/advicers/show_advicers.php'
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