<template lang="html">
    <div>
        <h4>Student id: {{ student_id }}</h4>
        <h4>Name: {{ name }}</h4>
        <h4>Tel: {{ tel }}</h4>
        <h4>Gender: {{ gender }}</h4>
        <h4>Birthday: {{ birthday }}</h4>
        <h4>Nationality: {{ nationality }}</h4>
    </div>
</template>
<script>
export default {
    data() {
        return {
            student_id: '',
            name: 'fname' + '  ' + 'lname',
            tel: '0987654321',
            gender: 'm',
            birthday: '12/03/1999',
            nationality: 'thai'
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
<style lang="css">
    
</style>