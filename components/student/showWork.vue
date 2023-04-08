<template lang="html">
    <div>
        <h3>Homework</h3>
        <ul v-for="item in work" :key="item.work_id">
            <li>{{ item.subject_id }}</li><p><b class="green--text">{{ item.work_name }}</b>:{{ item.work_details }}</p><p class="green">Deadline:{{ item.deadline }}</p>
            <v-divider></v-divider>
        </ul>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    data() {
        return {
            work: []
        }
    },
    mounted() {
        this.storage();
        axios.get('http://localhost/service_ip3/student/work.php',{params: {id:this.student_id}})
          .then((resp) => {
            this.work = resp.data.response
          });
    },
    methods: {
        storage(){
            this.student_id = sessionStorage.getItem('user_id')
        }        
    },
}
</script>
<style lang="css">
    
</style>