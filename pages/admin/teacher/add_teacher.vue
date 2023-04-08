<template lang="heml">
    <div>
        <h2>ADD TEACHER</h2>
        <v-form actions=''>
            <v-row>
                <v-col>
                    <v-text-field v-model="teacher_id" color="primary" label="Teacher ID" variant="underlined"></v-text-field>
                    <v-text-field v-model="password" color="primary" label="password" variant="underlined" type="password"></v-text-field>
                    <v-text-field v-model="first_name" color="primary" label="First name" variant="underlined"></v-text-field>
                    <v-text-field v-model="last_name" color="primary" label="Last name" variant="underlined"></v-text-field>
                    <v-radio-group v-model="gender" inline label='Gender'>
                      <v-radio label="Male" value="M"></v-radio>
                      <v-radio label="Female" value="F"></v-radio>
                    </v-radio-group>
                    <v-text-field v-model="social_id" color="primary" label="Social id" variant="underlined"></v-text-field>
                    <v-text-field v-model="bathday" color="primary" label="Bathday" variant="underlined" type="date" hint="YYYY/MM/DD format"></v-text-field>
                    <v-text-field v-model="nationality" color="primary" label="nationality" variant="underlined"></v-text-field>
                  </v-col>
                  <v-col>
                  <v-text-field v-model="phone_number" color="primary" label="Phone number" variant="underlined"></v-text-field>
                  <v-text-field v-model="first_name_father" color="primary" label="Father first name" variant="underlined"></v-text-field>
                  <v-text-field v-model="last_name_father" color="primary" label="Father last name" variant="underlined"></v-text-field>
                  <v-text-field v-model="first_name_mother" color="primary" label="Mother first name" variant="underlined"></v-text-field>
                  <v-text-field v-model="last_name_mother" color="primary" label="Mother last name" variant="underlined"></v-text-field>
                  <v-text-field v-model="fist_name_parent" color="primary" label="Parent first name" variant="underlined"></v-text-field>
                  <v-text-field v-model="last_name_parent" color="primary" label="Parent last name" variant="underlined"></v-text-field>
                  <v-text-field v-model="phone_number_of_parent" color="primary" label="Phone number of parent" variant="underlined"></v-text-field>
                </v-col>
            </v-row>
            <v-btn color="success" class='mx-3' @click="handleSubmit()">submit</v-btn>
            <v-btn color="red" type='reset'>clear</v-btn>
        </v-form>
    </div>
</template>
<script>
import MD5 from "crypto-js/md5";
import axios from 'axios';
export default {
  layout: 'admin',
  data() {
    return {
      inline: null,
      teacher_id: '',
      password: '',
      first_name: '',
      last_name: '',
      gender: '',
      social_id: '',
      bathday: '',
      nationality: '',
      phone_number: '',
      first_name_father: '',
      last_name_father: '',
      first_name_mother: '',
      last_name_mother: '',
      fist_name_parent: '',
      last_name_parent: '',
      phone_number_of_parent: ''
    }
  },
  created(){
    this.generateTeacherID()
  },
  methods: {
    handleSubmit() {
      this.password = MD5(this.password).toString()
      axios.post('http://localhost/service_ip3/admin/teacher/add_teacher.php',
        {
          teacher_id: this.teacher_id,
          password: this.password,
          first_name: this.first_name,
          last_name: this.last_name,
          gender: this.gender,
          social_id: this.social_id,
          bathday: this.bathday,
          nationality: this.nationality,
          phone_number: this.phone_number,
          first_name_father: this.first_name_father,
          last_name_father: this.last_name_father,
          first_name_mother: this.first_name_mother,
          last_name_mother: this.last_name_mother,
          first_name_parent: this.fist_name_parent,
          last_name_parent: this.last_name_parent,
          phone_number_of_parent: this.phone_number_of_parent,
          status_id: 1,
        }
      ).then((resp) => {
        // console.log(resp.data);
      })
    },
    generateTeacherID() {
      axios.get('http://localhost/service_ip3/admin/teacher/get_last_teacher_id.php').then((resp) => {
            this.teacher_id = 'T' + (parseInt(resp.data.response.teacher_id.substr(1, 6)) + 1).toString()
            // console.log(resp.data.response.teacher_id);
        })
    }
  }
}
</script>
<style lang="css"></style>