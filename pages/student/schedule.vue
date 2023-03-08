<template lang="HTML">
    <div>
        <v-card class=text-center>
            <h1>Class/room</h1>
            <h3>year</h3>
            <h4>Advisor</h4>
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
                    <tr
                      v-for="item in days"
                      :key="item.name"
                    >
                      <td>{{ item.name }}</td>
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
                ]
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