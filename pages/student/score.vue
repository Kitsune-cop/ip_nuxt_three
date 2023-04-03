<template lang="HTML">
    <div>
        <v-card class=text-center>
            <h3>Score table</h3>
            <!-- <v-card-subtitle>Schoolyear:{{score[0].school_year}}<br>Class:{{score[0].grade}}/{{score[0].room}}</v-card-subtitle> -->

            <v-simple-table >
                <template v-slot:default>
                  <thead>
                    <tr>
                      <th>
                        ชื่อวิชา
                      </th>
                      <th >
                        รายละเอียด
                      </th>
                      <th >
                        คะแนนเต็ม
                      </th>
                      <th >
                        คะแนนที่ได้
                      </th>
                      <th >
                        %
                      </th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr v-for="(item,i) in score" :key="i">
                      <td>{{item.subject_name}}</td>
                      <td>{{item.score_evaluation}}</td>
                      <td>{{item.max_score}}</td>
                      <td>{{item.point}}</td>
                      <td>{{item.percent}}</td>
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
        data()  {
            return {
                student_id:'',
                score: []
            }
        },
        mounted() {
          this.storage();

          axios.get('http://localhost/service_ip3/student/score.php',{params: {id:this.student_id}})
          .then((resp) => {
            this.score = resp.data.response
          });
        },
        methods: {
          storage(){
            this.student_id = sessionStorage.getItem('user_id')
          }        
        },
    }
</script>