<template lang="heml">
    <div>
        <h2>ADD STUDENT</h2>
        <v-form>
            <v-row>
                <v-col>
                    <v-text-field v-model="student_id" color="primary" label="Student ID" variant="underlined"></v-text-field>
                    <v-text-field v-model="password" color="primary" label="password" variant="underlined" type="password"></v-text-field>
                    <v-text-field v-model="first_name" color="primary" label="First name" variant="underlined"></v-text-field>
                    <v-text-field v-model="last_name" color="primary" label="Last name" variant="underlined"></v-text-field>
                    <v-radio-group v-model="gender" inline label='Gender'>
                      <v-radio label="Male" value="M"></v-radio>
                      <v-radio label="Female" value="F"></v-radio>
                    </v-radio-group>
                    <v-text-field v-model="bathday" color="primary" label="Bathday" variant="underlined" type="date" hint="YYYY/MM/DD format"></v-text-field>
                    <v-text-field v-model="nationality" color="primary" label="nationality" variant="underlined"></v-text-field>
                  </v-col>
                  <v-col>
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
import axios from 'axios';
export default {
  layout: 'admin',
  data() {
    return {
      inline: null,
      student_id: '',
      password: '',
      first_name: '',
      last_name: '',
      gender: '',
      bathday: '',
      nationality: '',
      first_name_father: '',
      last_name_father: '',
      first_name_mother: '',
      last_name_mother: '',
      fist_name_parent: '',
      last_name_parent: '',
      phone_number_of_parent: '',
    }
  },
  methods: {
    handleSubmit() {
      this.url = 'http://localhost/service/admin/add_student.php?student_id="'
        axios.get(this.url).then((resp) => {
            // console.log(resp.data.response)
            this.desserts = resp.data.response
        })
    }
  }
}
</script>
<style lang="css"></style>