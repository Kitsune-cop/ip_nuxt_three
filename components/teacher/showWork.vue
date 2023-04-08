<template lang="html">
    <div>
        <v-row>
            <v-col cols="8">
                <h3>Homework</h3>
                <v-btn class="success" to="/teacher/add_work">
                    <v-icon dark>mdi-plus</v-icon>
                    <!-- ADD WORK -->
                </v-btn>
            </v-col>

            <v-col cols="12">
                <v-divider></v-divider>
                 <ul v-for="item in work" :key="item.work_id">
                <v-col>
                    <li>{{ item.subject_id }}</li><p><b class="red--text">{{ item.work_name }}:</b>{{ item.work_details }}</p><p class="red">Deadline:{{ item.deadline }}</p>
                    <v-btn class="warning"  @click="handleClicked(item.work_id)"><v-icon>
                        mdi-pencil
                    </v-icon>
                    <!-- EDIT -->
                    </v-btn>
                </v-col>
                <v-divider></v-divider>
                </ul>
            </v-col>
           
        </v-row>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    data() {
        return {
            teacher_id:'',
            work: []
        }
    },
    mounted() {
        this.storage();
        axios.get('http://localhost/service_ip3/teacher/work.php',{params: {id:this.teacher_id}})
          .then((resp) => {
            this.work = resp.data.response
          });
    },
    methods: {
        storage(){
            this.teacher_id = sessionStorage.getItem('user_id')
        },
        handleClicked(item) {
            sessionStorage.setItem('work_id', item)
            window.location = '/teacher/edit_work'
            // console.log(item)// eslint-disable-next-line no-console
        }     
    },
}
</script>
<style lang="css">
    
</style>