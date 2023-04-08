<template lang="">
<v-container>
    
    <h1 class="my-5">School year {{ params.school_year }} Grade {{ params.grade }} Room {{ params.room }}</h1>
    <v-col cols="auto">
      <v-dialog
        transition="dialog-top-transition"
        max-width="600"
      >
        <template v-slot:activator="{ on, attrs }">
                <v-btn
                color="primary"
                v-bind="attrs"
                v-on="on"
              >Add advicer</v-btn>
            </template>
        <template v-slot:default="dialog">
          <v-card>
            <!-- <v-toolbar
              color="primary"
              dark
            >Opening from the top</v-toolbar> -->
            <v-card-text>
              <div class="text-h2 py-12">Add advicer</div>
              <v-form v-model="valid">
                <v-combobox
                    v-model="select"
                    :items="teacher"
                    :search-input.sync="search"
                    hide-selected
                    label="Input teacher"
                    small-chips
                >
                </v-combobox>
                <v-card-actions class="justify-end">
                    <v-btn color="success" @click="handle_submit()">submit</v-btn>
                  <v-btn
                    color="error"
                    @click="dialog.value = false"
                  >cancel</v-btn>
                </v-card-actions>
            </v-form>
            </v-card-text>
          </v-card>
        </template>
      </v-dialog>
    </v-col>
  </v-row>
    <v-row>
    {{ select }}
</v-row>
    <v-row dense>
        <v-col
            v-for="(teacher) in data" 
            :key='teacher.teacher_id'
            cols = "6"
        >
        <v-card
            class="ma-3 py-2 px-3"
            elevation="9"
            outlined
        >
        {{ teacher.teacher_id }}
        {{ teacher.first_name }}
        {{ teacher.last_name }}
        </v-card>
        </v-col>
    </v-row>
</v-container>
</template>
<script>
import axios from 'axios';
export default {
    layout: 'admin',
    data() {
        return {
            data: [],
            params: {
                school_year: '',
                grade: '',
                room: '',
                teacher_id: ''
            },
            select: '',
            search: null,
            teacher: []
        }
    },
    methods: {
        handle_submit() {
            this.select = this.select.split(' ')[0]
            this.params.teacher_id = this.select
            // console.log(this.params);
            axios.post('http://localhost/service_ip3/admin/advicers/add_advicers.php',
            this.params)
            .then((resp) => {
                console.log(resp);
            })
        }
    },
    created() {
        this.params.school_year = this.$route.query.school_year;
        this.params.grade = this.$route.query.grade;
        this.params.room = this.$route.query.room;
        console.log(this.params);
        axios.get('http://localhost/service_ip3/admin/advicers/show_name_advicers.php',
        { params: this.$route.query })
        .then((resp) => {
            this.data = resp.data.response
            // console.log(resp);
        })
        .catch(function (error) {
            console.log(error);
        });
        axios.post('http://localhost/service_ip3/admin/advicers/add_advicers.php', {
            school_year: '2019',
            grade: '1',
            room: '4',
            teacher_id: 'T15255'
        })
        .then((resp) => {
            // console.log(resp.data);
            // console.log(resp);
        });
        axios.get('http://localhost/service_ip3/admin/teacher/show_teacher_name.php')
            .then((resp) => {
                // console.log(resp.data.response);
                for (const item of resp.data.response) {
                    // this.teacher.push(item)
                    this.teacher.push(Object.values(item).join(' '))
                }
            });
    }
}
</script>
<style lang="">
    
</style>