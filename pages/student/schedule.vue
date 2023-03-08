<template lang="HTML">
    <div>
        <v-card class=text-center>
            <h3>Schedule</h3>
            <!-- <v-card-subtitle>Schoolyear:{{ datas[0].school_year }}<br>Advisor:{{ teas[0].fist_name}}&nbsp;{{ teas[0].last_name}}
              <br>class:{{datas[0].grade}}/{{datas[0].room}}</v-card-subtitle> -->
            <v-simple-table >
                <template v-slot:default>
                  <thead>
                    <tr>
                      <th >
                        Day/Time
                      </th>
                      <th v-for="item in times" :key="item.name">
                        {{item.name}}
                      </th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr v-for="item in days" :key="item.name">
                      <td>{{ item.name }}</td>
                      <td v-for="(time,i) in times" :key="i"> {{table[i].subject_id}}</td>
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
        layout: 'user',
        data:() =>  ({
                student_id: '',
                days: [
                    {name: 'Monday',},
                    {name: 'Tuesday',},
                    {name: 'Wednesday',},
                    {name: 'Thursday',},
                    {name: 'Friday',},
                ],

                times: [
                    {name: '08.00-09.50'},
                    {name: '10.00-10.50'},
                    {name: '11.00-11.50'},
                    {name: '13.00-13.50'},
                    {name: '14.00-14.50'},
                    {name: '15.00-15.50'},
                ],
                datas: [],
                teas: [],
                table: [],

        }),

        mounted() {
          this.storage();
          axios.get('http://localhost/service/student/info.php',{params: {id:this.student_id}})
          .then((resp) => {
            this.datas = resp.data.response
          });
          // console.log(this.datas)// eslint-disable-line no-console
          axios.get('http://localhost/service/student/advicers.php',{params: {id:this.student_id}})
          .then((resp) => {
            this.teas = resp.data.response
          });
          axios.get('http://localhost/service/student/schedule.php',{params: {id:this.student_id}})
          .then((resp) => {
            this.table = resp.data.response
          });
        },
        
        methods: {
          storage(){
            this.student_id = sessionStorage.getItem('user_id')
          }        
        },
    }
</script>