<template lang="HTML">
    <div>
        <v-card class=text-center>
            <h3>Score table</h3>
            <!-- <v-card-subtitle>Schoolyear:{{score[0].school_year}}<br>Class:{{score[0].grade}}/{{score[0].room}}</v-card-subtitle> -->
            <v-select
            :items="items"
            filled
            label="เลือกวิชา"
            class="pa-5"
            ></v-select>
            <v-simple-table >
                <template v-slot:default>
                  <thead>
                    <tr>
                        <th>
                            ลำดับที่
                        </th>
                        <th>
                            ชื่อ-นามสกุล
                        </th>
                        <th></th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr>
                        <td>1</td>
                        <td>name</td>
                        <td>
                            <v-btn class="green accent-3" to="/teacher/view_score">VIEW SCORE</v-btn>
                            <v-btn class="red accent-3" to="/teacher/view_score">ADD SCORE</v-btn>
                        </td>
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
        data:() => ({
                items: ['Foo', 'Bar', 'Fizz', 'Buzz'],
                student_id:'',
                score: []
        }),
        mounted() {
          this.storage();
        //   axios.get('http://localhost/service/student/score.php',{params: {id:this.student_id}})
        //   .then((resp) => {
        //     this.score = resp.data.response
        //   });
        },
        methods: {
          storage(){
            this.teacher_id = sessionStorage.getItem('user_id')
          }        
        },
    }
</script>

