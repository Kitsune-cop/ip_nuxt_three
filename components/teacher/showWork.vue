<template lang="html">
    <div>
        <h3>Homework</h3>
        <ul v-for="item in work" :key="item.work_id">
            <li>{{ item.subject_id }}</li><p><b class="red--text">{{ item.work_name }}:</b>{{ item.work_details }}</p><p class="red">Deadline:{{ item.deadline }}</p>
            <v-divider></v-divider>
        </ul>
        <v-btn class="success" to="/teacher/add_work">
            ADD WORK
        </v-btn>
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
        axios.get('http://localhost/service/teacher/work.php',{params: {id:this.teacher_id}})
          .then((resp) => {
            this.work = resp.data.response
          });
    },
    methods: {
        storage(){
            this.teacher_id = sessionStorage.getItem('user_id')
        }        
    },
}
</script>
<style lang="css">
    
</style>