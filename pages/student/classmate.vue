<template lang="HTML">
    <div>
        <v-card class=text-center>
            <h3>Classmate</h3>
            <v-card-subtitle>School Year<br>Advisor<br>class/room</v-card-subtitle>
            <v-simple-table >
                <template v-slot:default>
                  <thead>
                    <tr>
                      <th >
                      </th>
                      <th>
                      </th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr>
                      <td></td>
                    </tr>
                  </tbody>
                </template>
            </v-simple-table>
        </v-card>
    </div>
</template>
<script>
    export default{
        layout: 'user',
        data()  {
            return {
                
            }
        },
        mounted() {
          this.storage();
        },
        methods: {
          storage(){
            this.student_id = sessionStorage.getItem('user_id')
          }        
        },
    }
</script>