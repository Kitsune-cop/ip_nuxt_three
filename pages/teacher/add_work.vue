<template lang="HTML">
    <div>
        <v-card class="text-center pa-10">
            <h3>ADD WORK</h3>
            <v-form actions=''>
                <v-row>
                    <v-col>
                        <v-text-field v-model="work_name" color="primary" label="Work Name" variant="underlined" ></v-text-field>
                        <v-text-field v-model="work_details" color="primary" label="Work Details" variant="underlined"></v-text-field>
                        <v-text-field v-model="data_form.subject_id" color="primary" label="Subject ID" disabled variant="underlined"></v-text-field>
                        <v-text-field v-model="data_form.subject_name" color="primary" label="Subject Name" disabled variant="underlined"></v-text-field>
                    </v-col>     
                    <v-col>
                        <v-text-field v-model="data_form.grade" color="primary" label="Grade" disabled variant="underlined"></v-text-field>
                        <v-text-field v-model="data_form.room" color="primary" label="Room" disabled variant="underlined" ></v-text-field>
                        <v-menu
                        v-model="menu2"
                        :close-on-content-click="false"
                        transition="scale-transition"
                        offset-y
                        max-width="290px"
                        min-width="auto"
                      >
                        <template v-slot:activator="{ on, attrs }">
                          <v-text-field
                            v-model="computedDateFormatted"
                            label="Dead line"
                            hint="MM/DD/YYYY"
                            persistent-hint
                            prepend-icon="mdi-calendar"
                            readonly
                            v-bind="attrs"
                            v-on="on"
                          ></v-text-field>
                        </template>
                        <v-date-picker
                          v-model="date"
                          no-title
                          @input="menu2 = false"
                        ></v-date-picker>
                      </v-menu>
                    </v-col>      
                </v-row>
                <v-btn color="success" class='mx-3' @click="handleSubmit()">submit</v-btn>
                <v-btn color="red" type='reset'>clear</v-btn>
            </v-form>
        </v-card>
    </div>
</template>
<script>
import axios from 'axios';
    export default{
      layout: 'teacher/user',
        data:vm =>  ({
                time_table_id:'',
                teacher_id: '',
                work_name:'',
                work_details:'',
                subject_id:'',
                grade:'',
                room:'',  
                date: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
                dateFormatted: vm.formatDate((new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10)),
                menu2: false,
                data_form: [],
        }),
        computed: {
            computedDateFormatted () {
                return this.formatDate(this.date)
            },
        },
        watch: {
            date (val) {
                this.dateFormatted = this.formatDate(this.date)
            },
        },
        created(){
          this.time_table_id = this.$route.query.tb_id;
        },
        mounted() {
            this.storage();
        
            axios.get('http://localhost/service_ip3/teacher/show_for_addW.php',{params: {tb_id:this.time_table_id}})
            .then((resp) => {
                this.data_form = resp.data.response[0]
                // console.log(this.data_form)// eslint-disable-next-line no-console
            });
            
        },
        methods: {
            handleSubmit() {
                axios.post('http://localhost/service_ip3/teacher/add_work.php',
                    {
                        // teacher_id: this.teacher_id,
                        work_name: this.work_name,
                        work_details: this.work_details,
                        date: this.date, 
                        enroll_subject_id: this.data_form.enroll_subject_id 
                    }   
                )
                .then((res)=>{
                        // console.log(res.data)// eslint-disable-next-line no-console
                    })
                
            },
            formatDate (date) {
                if (!date) return null

                const [year, month, day] = date.split('-')
                return `${month}/${day}/${year}`
            },
            parseDate (date) {
                if (!date) return null

                const [month, day, year] = date.split('/')
                return `${year}-${month.padStart(2, '0')}-${day.padStart(2, '0')}`
            },
          storage(){
            this.teacher_id = sessionStorage.getItem('user_id')
          }        
        },
    }
</script>