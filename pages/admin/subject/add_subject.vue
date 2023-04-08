<template lang="heml">
    <div>
        <h2>ADD SUBJECT</h2>
        <v-form actions=''>
            <v-row>
                <v-col>
                    <v-text-field v-model="subject_id" v-on:input="handle_check_duplicate_id()" :hint="errormessages" :color="color" label="Subject ID" variant="underlined"></v-text-field>
                    <v-text-field v-model="subject_name" color="primary" label="Subject name" variant="underlined"></v-text-field>
                    <v-textarea
                      v-model="course_description_th"
                      solo
                      name="input-7-4"
                      label="Course description th"
                    ></v-textarea>
                    <v-textarea
                      v-model="course_description_en"
                      solo
                      name="input-7-4"
                      label="Course description en"
                    ></v-textarea>
                </v-col>
            </v-row>
            <v-btn color="success" class='mx-3' @click="handleSubmit()">submit</v-btn>
            <v-btn color="red" type='reset'>clear</v-btn>
        </v-form>
    </div>
</template>
<script>
import axios from 'axios';
export default {
  layout: 'admin',
  data() {
    return {
      inline: null,
      subject_id: '',
      subject_name: '',
      course_description_th: '',
      course_description_en: '',
      errormessages: '',
      color: 'primary',
    }
  },
  methods: {
    handleSubmit() {
      axios.post('http://localhost/service_ip3/admin/subject/add_subject.php',
        {
          subject_id: this.subject_id,
          subject_name: this.subject_name,
          course_description_th: this.course_description_th,
          course_description_en: this.course_description_en
        }
      )
  },
  handle_check_duplicate_id(){
    axios
    .get('http://localhost/service_ip3/admin/subject/check_subject_id.php?subject_id=' + this.subject_id)
    .then((resp) => {
      // console.log(resp)
      this.errormessages = ''
      this.color = 'primary'
    })
    .catch(()=>{
      this.errormessages = 'Duplicate ID'
      this.color = 'red'
    })
  }
}
}
</script>
<style lang="css"></style>