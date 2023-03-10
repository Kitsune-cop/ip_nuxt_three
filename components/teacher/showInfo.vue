<template lang="html">
    <div>
        <h4>Teacher id: {{ teacher_id }}</h4>
        <h4>Name: {{ tea[0].fist_name }}&nbsp;{{ tea[0].last_name }}</h4>
        <h4>Tel: {{ tea[0].phone_number }}</h4>
        <h4>Gender: {{ tea[0].gender }}</h4>
        <h4>Birthday: {{ tea[0].bathday }}</h4>
        <h4>Nationality: {{ tea[0].nationality }}</h4>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    data: () => ({
            teacher_id: '',
            tea: [{
                teacher_id:'',
                password:'',
                fist_name:'',
                last_name:'',
                gender:'',
                solial_id:'',
                bathday:'',
                nationality:'',
                phone_number:'',
                first_name_father:'',
                last_name_father:'',
                first_name_mother:'',
                last_name_mother:'',
                fist_name_parent:'',
                last_name_parent:'',
                phone_number_of_parent:'',
                status_id:'',
                school_year:'',
                grade:'',
                room:''

            }]
    }),
    mounted() {
        this.storage();
        axios.get('http://localhost/service/teacher/info.php',{params: {id:this.teacher_id}})
        .then((resp) => {
            this.tea = resp.data.response
        })
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