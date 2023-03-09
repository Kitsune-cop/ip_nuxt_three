<template lang="heml">
    <div>
        <h2>EDIT TEACHER</h2>
        <v-form actions=''>
            <v-row>
                <v-col>
                    <v-text-field v-model="detial[0].teacher_id" color="primary" label="Teacher ID" variant="underlined"></v-text-field>
                    <v-text-field v-model="detial[0].password" color="primary" label="password" variant="underlined" type="password"></v-text-field>
                    <v-text-field v-model="detial[0].first_name" color="primary" label="First name" variant="underlined"></v-text-field>
                    <v-text-field v-model="detial[0].last_name" color="primary" label="Last name" variant="underlined"></v-text-field>
                    <v-radio-group v-model="detial[0].gender" inline label='Gender'>
                      <v-radio label="Male" value="M"></v-radio>
                      <v-radio label="Female" value="F"></v-radio>
                    </v-radio-group>
                    <v-text-field v-model="detial[0].social_id" color="primary" label="Social id" variant="underlined"></v-text-field>
                    <v-text-field v-model="detial[0].bathday" color="primary" label="Bathday" variant="underlined" type="date" hint="YYYY/MM/DD format"></v-text-field>
                    <v-text-field v-model="detial[0].nationality" color="primary" label="nationality" variant="underlined"></v-text-field>
                  </v-col>
                  <v-col>
                  <v-text-field v-model="detial[0].phone_number" color="primary" label="Phone number" variant="underlined"></v-text-field>
                  <!-- <v-text-field v-model="detial[0].first_name_father" color="phone_number" label="Phone number" variant="underlined"></v-text-field> -->
                  <v-text-field v-model="detial[0].first_name_father" color="primary" label="Father first name" variant="underlined"></v-text-field>
                  <v-text-field v-model="detial[0].last_name_father" color="primary" label="Father last name" variant="underlined"></v-text-field>
                  <v-text-field v-model="detial[0].first_name_mother" color="primary" label="Mother first name" variant="underlined"></v-text-field>
                  <v-text-field v-model="detial[0].last_name_mother" color="primary" label="Mother last name" variant="underlined"></v-text-field>
                  <v-text-field v-model="detial[0].first_name_parent" color="primary" label="Parent first name" variant="underlined"></v-text-field>
                  <v-text-field v-model="detial[0].last_name_parent" color="primary" label="Parent last name" variant="underlined"></v-text-field>
                  <v-text-field v-model="detial[0].phone_number_of_parent" color="primary" label="Phone number of parent" variant="underlined"></v-text-field>
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
        detial: [{
        bathday: '',
        first_name: '',
        first_name_father: '',
        first_name_mother: '',
        first_name_parent: '',
        gender: '',
        last_name: '',
        last_name_father: '',
        last_name_mother: '',
        last_name_parent: '',
        nationality: '',
        password: '',
        phone_number: '',
        phone_number_of_parent: '',
        social_id: '',
        status_id: '',
        teacher_id: '',
      }]
    }
  },
  created(){
    axios.get('http://localhost/service/admin/show_data_teacher.php', {params :{teacher_id: this.$route.hash.substr(1, 6)}})
      .then((resp) => {
        this.detial = resp.data.response
        this.detial[0].password = ''
        // console.log(this.detial[0]);
      })
    },
    methods: {
      handleSubmit() {
        this.detial[0].password = MD5(this.detial[0].password).toString()
        axios.post('http://localhost/service/admin/update_teacher.php',
        {
          teacher_id: this.detial[0].teacher_id,
          password: this.detial[0].password,
          first_name: this.detial[0].first_name,
          last_name: this.detial[0].last_name,
          gender: this.detial[0].gender,
          social_id: this.detial[0].social_id,
          bathday: this.detial[0].bathday,
          nationality: this.detial[0].nationality,
          phone_number: this.detial[0].phone_number,
          first_name_father: this.detial[0].first_name_father,
          last_name_father: this.detial[0].last_name_father,
          first_name_mother: this.detial[0].first_name_mother,
          last_name_mother: this.detial[0].last_name_mother,
          first_name_parent: this.detial[0].first_name_parent,
          last_name_parent: this.detial[0].last_name_parent,
          phone_number_of_parent: this.detial[0].phone_number_of_parent,
          status_id: 1,
        }
        )
        .then((resp)=>{
          console.log(resp.data)
        })
    }
  }
}
</script>
<style lang="css"></style>