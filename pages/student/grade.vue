<template lang="HTML">
    <div>
        <v-card class=text-center>
            <h3>Grade</h3>
            <v-card-subtitle>class/room</v-card-subtitle>
            <v-simple-table >
                <template v-slot:default>
                  <thead class="text-center">
                    <tr>
                      <th span="3 col">
                        Schoolyear
                      </th>
                    </tr>
                    <tr>
                      <th>
                        Code sub
                      </th>
                      <th>
                        name sub
                      </th>
                      <th>
                        grade
                      </th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr>
                      <td>
                        {{grade}}
                      </td>
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
                grade: []
            }
        },
        created(){
            this.storage();
            axios.get('http://localhost/service/student/grade.php',{params :{id:this.student_id}})
            .then((resp) => {
              this.grade = resp.data.response
            });
            // console.log(this.grade)// eslint-disable-line no-console
        },
        methods: {
          storage(){
            this.student_id = 'S15523'
          },    
          // geva(){
          //   console.log(this.grade)// eslint-disable-line no-console
          // }   
        },
    }
</script>