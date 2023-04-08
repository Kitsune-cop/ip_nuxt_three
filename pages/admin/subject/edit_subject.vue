<template lang="heml">
  <div>
      <h2>ADD SUBJECT</h2>
      <v-form actions=''>
          <v-row>
              <v-col>
                  <v-text-field v-model="detial[0].subject_id" v-on:input="handle_check_duplicate_id()" :hint="errormessages" color="primary" label="Subject ID" variant="underlined"></v-text-field>
                  <v-text-field v-model="detial[0].subject_name" color="primary" label="Subject name" variant="underlined"></v-text-field>
                  <v-textarea
                    v-model="detial[0].course_description_th"
                    solo
                    name="input-7-4"
                    label="Course description th"
                  ></v-textarea>
                  <v-textarea
                    v-model="detial[0].course_description_en"
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
      detial: [{
        subject_id: '',
        subject_name: '',
        course_description_th: '',
        course_description_en: '',
      }],
      errormessages: '',
    }
  },
  created(){
    axios.get('http://localhost/service_ip3/admin/subject/show_data_subject.php', {params :{subject_id: this.$route.hash.substr(1, 6)}})
      .then((resp) => {
        this.detial = resp.data.response
        // console.log(this.detial[0]);
      })
    },
    methods: {
      handleSubmit() {
        axios.post('http://localhost/service_ip3/admin/subject/update_student.php',
        {
          subject_id: this.detial[0].subject_id,
          subject_name: this.detial[0].subject_name,
          course_description_th: this.detial[0].course_description_th,
          course_description_en: this.detial[0].course_description_en,
        }
        )
        .then((resp)=>{
          // console.log(resp.data)
        })
    },
  }
}
</script>
<style lang="css"></style>