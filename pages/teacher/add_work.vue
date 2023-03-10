<template lang="HTML">
    <div>
        <v-card class="text-center pa-10">
            <h3>ADD WORK</h3>
            <v-form actions=''>
                <v-row>
                    <v-col>
                        <v-text-field v-model="work_name" color="primary" label="Work Name" variant="underlined" type="password"></v-text-field>
                        <v-text-field v-model="work_details" color="primary" label="Work Details" variant="underlined"></v-text-field>
                        <v-text-field v-model="subject_id" color="primary" label="Subject ID" variant="underlined"></v-text-field>
                    </v-col>     
                    <v-col>
                        <v-text-field v-model="grade" color="primary" label="Class" variant="underlined"></v-text-field>
                        <v-text-field v-model="room" color="primary" label="Room" variant="underlined" type="password"></v-text-field>
                    </v-col>      
                </v-row>
                <v-btn color="success" class='mx-3' @click="handleSubmit()">submit</v-btn>
                <v-btn color="red" type='reset'>clear</v-btn>
            </v-form>
        </v-card>
    </div>
</template>
<script>
import axios from 'axios'
    export default{
      layout: 'teacher/user',
        data:() =>  ({
                teacher_id: '',
                work_name:'',
                work_details:'',
                subject_id:'',
                grade:'',
                room:'',  
        }),
        // created(){
        //   this.getInfo()
        //   this.getAdvciers()
        //   this.getSche()
        // //   console.log(this.datas)// eslint-disable-next-line no-console
        // },
        mounted() {
        this.storage();
        },
        methods: {
            handleSubmit() {
            axios.post('http://localhost/service/admin/add_student.php',
                {
                    teacher_id: '',
                    work_name:'',
                    work_details:'',
                    subject_id:'',
                    grade:'',
                    room:'',  
                }
            )
            },
          storage(){
            this.student_id = sessionStorage.getItem('user_id')
          }        
        },
    }
</script>