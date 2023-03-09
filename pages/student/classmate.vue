<template lang="HTML">
    <div>
        <v-card class=text-center>
            <h3>Classmate</h3>
            <!-- <v-card-subtitle>School Year:{{user[0].school_year}}<br>Advisor:{{teas[0].fist_name}}&nbsp;{{teas[0].last_name}}<br>class:{{stu[0].grade}}/{{stu[0].room}}</v-card-subtitle> -->
            <v-simple-table >
                <template v-slot:default>
                  <thead>
                    <tr >
                      <th class="text-center">
                        ลำดับที่
                      </th>
                      <th class="text-center">
                        รหัสนักเรียน
                      </th>
                      <th class="text-center">
                        ชื่อ-นานสกุล
                      </th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr v-for="(item,i) in stu" :key="i">
                      <td>{{i+1}}</td>
                      <td>{{stu[i].student_id}}</td>
                      <td>{{stu[i].fist_name}}&nbsp;{{stu[i].last_name}}</td>
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
        data()  {
            return {
                student_id:'',
                user: [],
                stu: [],
                teas: [],
            }
        },
        mounted() {
          
          this.storage();
          axios.get('http://localhost/service/student/info.php',{params: {id:this.student_id}})
          .then((resp) => {
              this.user = resp.data.response  
          });
          axios.get('http://localhost/service/student/advicers.php',{params: {id:this.student_id}})
          .then((resp) => {
            this.teas = resp.data.response
          });
          console.log(this.user[0])// eslint-disable-line no-console
          axios.get('http://localhost/service/student/classmate.php',{params: {class:'1',room:'1'}})
          .then((resp) => {
            this.stu = resp.data.response
          });
          
        },
        methods: {
          storage(){
            this.student_id = 'S15523'
          }        
        },
    }
</script>