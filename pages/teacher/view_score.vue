<template lang="HTML">
    <div>
        <v-card class=text-center>
            <h3>Score table</h3>
            <!-- <v-card-subtitle>Schoolyear:{{score[0].school_year}}<br>Class:{{score[0].grade}}/{{score[0].room}}</v-card-subtitle> -->
            ชื่อวิชา
            <v-simple-table >
                <template v-slot:default>
                  <thead>
                    <tr>
                      <th >
                        รายละเอียดคะแนน
                      </th>
                      <th >
                        คะแนนเต็ม
                      </th>
                      <th >
                        คะแนนที่ได้
                      </th>
                      <th >

                      </th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr>
                      <td></td>
                      <td></td>
                      <td></td>
                      <td><v-btn class="warning">EDIT SCORE</v-btn></td>
                    </tr>
                  </tbody>
                </template>
              </v-simple-table>
        </v-card>
    </div>
</template>
<script>
// import axios from 'axios'
    export default{
      layout: 'teacher/user',
        data()  {
            return {
                teacher_id:'',
                score: []
            }
        },
        mounted() {
          this.storage();

          // axios.get('http://localhost/service/teacher/info.php',{params: {id:this.teacher_id}})
          // .then((resp) => {
          //   this.score = resp.data.response
          // });
        },
        methods: {
          storage(){
            this.teacher_id = sessionStorage.getItem('user_id')
          }        
        },
    }
</script>