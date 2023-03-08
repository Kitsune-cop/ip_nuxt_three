<template lang="html">
    <div>
        <!-- <h4>Student id: {{ student_id }}</h4>
        <h4>Name: {{ stu[0].fist_name }}&nbsp;{{ stu[0].last_name }}</h4>
        <h4>Tel: {{ stu[0].phone_number }}</h4>
        <h4>Gender: {{ stu[0].gender }}</h4>
        <h4>Birthday: {{ stu[0].bathday }}</h4>
        <h4>Nationality: {{ stu[0].nationality }}</h4> -->
    </div>
</template>
<script>
import axios from 'axios'
export default {
    data: () => ({
            student_id: '',
            stu: []
    }),
    mounted() {
        this.storage();
        axios.get('http://localhost/service/student/info.php',{params: {id:this.student_id}})
        .then((resp) => {
            this.stu = resp.data.response
        })
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