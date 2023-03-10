<template lang="HTML">
    <div>
        <v-card class=text-center>
            <h3>Schedule</h3>
            <v-card-subtitle>Schoolyear:{{ datas[0].school_year }}<br>Advisor:{{ teas[0].fist_name}}&nbsp;{{ teas[0].last_name}}
              <br>class:{{datas[0].grade}}/{{datas[0].room}}</v-card-subtitle>
            <v-simple-table >
                <template v-slot:default>
                  <thead>
                    <tr>
                      <th >
                        Day/Time
                      </th>
                      <th v-for="(item,i) in times" :key="i">
                        {{item.name}}
                      </th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr v-for="(item,i) in days" :key="i">
                      <td>{{ item.name }}</td>
                      <!-- <td v-for="(time,i) in times" :key="i"> {{table[i].subject_id}}</td> -->
                    </tr>
     
                  </tbody>
                </template>
              </v-simple-table>
        </v-card>
    </div>
</template>
<script>
import axios from 'axios'
    export default{
      layout: 'student/user',
        data:() =>  ({
                student_id: 'S15523',
                days: [
                    {name: 'Monday',},
                    {name: 'Tuesday',},
                    {name: 'Wednesday',},
                    {name: 'Thursday',},
                    {name: 'Friday',},
                ],

                times: [
                    {time: '08.00-09.50'},
                    {time: '10.00-10.50'},
                    {time: '11.00-11.50'},
                    {time: '13.00-13.50'},
                    {time: '14.00-14.50'},
                    {time: '15.00-15.50'},
                ],
                datas: [{
                      student_id:'',
                      password:'',
                      fist_name:'',
                      last_name:'',
                      gender:'',
                      solial_id:'',
                      bathday:'',
                      nationality:'',
                      phone_number:'',
                      first_name_father:'',
                      last_name_father:'',
                      first_name_mother:'',
                      last_name_mother:'',
                      fist_name_parent:'',
                      last_name_parent:'',
                      phone_number_of_parent:'',
                      status_id:'',
                      school_year:'',
                      grade:'',
                      room:''

                }
                ],
                teas: [{
                    student_id: '',
                    school_year: '',
                    grade: '',
                    room: '',
                    teacher_id: '',
                    password: '',
                    fist_name: '',
                    last_name: '',
                    gender: '',
                    solial_id: '',
                    bathday: '',
                    nationality: '',
                    phone_number: '',
                    first_name_father: '',
                    last_name_father: '',
                    first_name_mother: '',
                    last_name_mother: '',
                    fist_name_parent: '',
                    last_name_parent: '',
                    phone_number_of_parent: '',
                    status_id: ''
                }
                ],
                table: [{
                    student_id:'',
                    school_year: '',
                    grade: '',
                    room: '',
                    time_table_id:'',
                    time: '',
                    term: '',
                    enroll_subject_id: '',
                    teacher_id: '',
                    subject_id: '',
                    },
                ],

        }),
        created(){
          this.getInfo()
          this.getAdvciers()
          this.getSche()
          // console.log(this.datas)// eslint-disable-next-line no-console
        },
        // mounted() {
        // this.storage();
        // },
        methods: {
          getInfo(){
            axios.get('http://localhost/service/student/info.php',{params: {id:this.student_id}})
            .then((resp) => {
              this.datas = resp.data.response
            });
          },
          getAdvciers(){
            axios.get('http://localhost/service/student/advicers.php',{params: {id:this.student_id}})
            .then((resp) => {
              this.teas = resp.data.response
            });
          },
          getSche(){
            axios.get('http://localhost/service/student/schedule.php',{params: {id:this.student_id}})
            .then((resp) => {
              this.table = resp.data.response
            });
          },
          // storage(){
          //   this.student_id = sessionStorage.getItem('user_id')
          // }        
        },
    }
</script>