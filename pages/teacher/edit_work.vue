<template lang="HTML">
    <div>
        <v-card class="text-center pa-10">
            <h3>EDIT WORK</h3>
            <v-form actions=''>
                <v-row>
                    <v-col>
                        <v-text-field v-model="details[0].work_name" color="primary" label="Work Name" variant="underlined" ></v-text-field>
                        <v-text-field v-model="details[0].work_details" color="primary" label="Work Details" variant="underlined"></v-text-field>
                        <v-text-field v-model="details[0].subject_id" color="primary" label="Subject ID"  disabled variant="underlined"></v-text-field>
                        <v-text-field v-model="details[0].subject_name" color="primary" label="Subject Name" disabled  variant="underlined"></v-text-field>
                    </v-col>     
                    <v-col>
                        <v-text-field v-model="details[0].grade" color="primary" label="Class" disabled variant="underlined"></v-text-field>
                        <v-text-field v-model="details[0].room" color="primary" label="Room" disabled variant="underlined" ></v-text-field>
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
            teacher_id: '',
            work_id:'',
            details: [{
                work_name:'',
                work_details:'',
                subject_id:'',
                subject_name:'',
                grade:'',
                room:'',  
                deadline:''
            }],
            det: [],
            date: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
            dateFormatted: vm.formatDate((new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10)),
            menu2: false,
                
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
        // created(){
        //     this.storage();
        //     axios.get('http://localhost/service_ip3/teacher/work_forEdit.php',{params: {id:this.work_id}})
        //     .then((resp) => {
        //         this.details = resp.data.response
        //         console.log(this.details)// eslint-disable-next-line no-console
        //     });
        // },
        mounted() {
            this.storage();
            axios.get('http://localhost/service_ip3/teacher/work_forEdit.php',{params: {id:this.work_id}})
            .then((resp) => {
                this.details = resp.data.response
                // console.log(this.details)// eslint-disable-next-line no-console
            });
        },
        methods: {
            handleSubmit() {
                axios.post('http://localhost/service_ip3/teacher/edit_work.php',
                    {
                        // teacher_id: this.teacher_id,
                        work_id: this.work_id,
                        work_name: this.details[0].work_name,
                        work_details: this.details[0].work_details,
                        subject_id: this.details[0].subject_id,
                        grade: this.details[0].grade,
                        room: this.details[0].room,
                        date: this.date,  
                    }   
                )
                .then((res)=>{
                        // console.log(res.data)// eslint-disable-next-line no-console
                })
                window.location = '/teacher'

                // console.log(this.subject_id)// eslint-disable-next-line no-console
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
            this.work_id = sessionStorage.getItem('work_id')
          }        
        },
    }
</script>