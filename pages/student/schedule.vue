<template lang="">
  <div>
      <v-container>
          <v-row>
              <h1 class="my-5">ตารางเรียน</h1>
          </v-row>
          <v-row>
              <v-col cols="1"></v-col>
              <v-col class="blue">08:00-09:00</v-col>
              <v-col class="blue">09:00-10:00</v-col>
              <v-col class="blue">10:00-11:00</v-col>
              <v-col class="blue">11:00-12:00</v-col>
              <v-col class="blue">12:00-13:00</v-col>
              <v-col class="blue">13:00-14:00</v-col>
              <v-col class="blue">14:00-15:00</v-col>
              <v-col class="blue">15:00-16:00</v-col>
          </v-row>
          <v-row class="">
              <v-col cols='1' class="cyan">MON</v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(0)">{{time_table[0].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(1)">{{time_table[1].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(2)">{{time_table[2].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(3)" >{{time_table[3].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="red text-body-2" outlined x-large disabled >LUNCH</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(4)">{{time_table[4].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(5)">{{time_table[5].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(6)">{{time_table[6].subject_id}}</v-btn></v-col>
          </v-row>
          <v-row>
              <v-col cols='1' class="cyan">TUE</v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(7)">{{time_table[7].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(8)">{{time_table[8].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(9)">{{time_table[9].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(10)">{{time_table[10].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="red text-body-2" outlined x-large disabled >LUNCH</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(11)">{{time_table[11].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(12)">{{time_table[12].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(13)">{{time_table[13].subject_id}}</v-btn></v-col>
          </v-row>
          <v-row>
              <v-col cols='1' class="cyan">WED</v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(14)">{{time_table[14].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(15)">{{time_table[15].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(16)">{{time_table[16].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(17)">{{time_table[17].subject_id}}</v-btn></v-col> 
              <v-col><v-btn class="red text-body-2" outlined x-large disabled>LUNCH</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(18)">{{time_table[18].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(19)">{{time_table[19].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(20)">{{time_table[20].subject_id}}</v-btn></v-col>
          </v-row>
          <v-row>
              <v-col cols='1' class="cyan">THU</v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(21)">{{time_table[21].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(22)">{{time_table[22].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(23)">{{time_table[23].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(24)">{{time_table[24].subject_id}}</v-btn></v-col>
              <v-col><v-btn outlined x-large disabled class="red text-body-2">LUNCH</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(25)">{{time_table[25].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(26)">{{time_table[26].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(27)">{{time_table[27].subject_id}}</v-btn></v-col>
          </v-row>
          <v-row>
              <v-col cols='1' class="cyan">FRI</v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(28)">{{time_table[28].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(29)">{{time_table[29].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(30)">{{time_table[30].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(31)">{{time_table[31].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="red text-body-2" outlined x-large disabled>LUNCH</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(32)">{{time_table[32].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(33)">{{time_table[33].subject_id}}</v-btn></v-col>
              <v-col><v-btn class="text-body-2" outlined x-large @click="handle(34)">{{time_table[34].subject_id}}</v-btn></v-col>
          </v-row> 
          <v-row>
                 <v-col ><v-text-field
                      id="subject_id"
                      v-model="data_form.subject_id"
                      name="subject_id"
                      label="Subject ID"
                      disabled
                      @:blur="get_subject_name()"
                      ></v-text-field></v-col>
                  <v-col ><v-text-field
                      id="subject_name"
                      v-model="data_form.subject_name"
                      name="subject_name"
                      label="Subject name"
                      disabled
                  ></v-text-field></v-col>
                  <v-col cols="6"><v-text-field
                      id="teacher_name"
                      v-model="data_form.teacher_name"
                      name="teacher_name"
                      label="Teacher name"
                      disabled
                  ></v-text-field></v-col> 
        </v-row>
      </v-container>
  </div>
</template>
<script>
import axios from 'axios';
export default {
  layout: 'student/user',
  data() {
      return {
          student_id: '',
          status_form: {
              expansion: false,
              index: ''
          },
          data_form: {
              subject_id: '',
              subject_name: '',
              school_year: '',
              grade: '',
              room: '',
              teacher_id: '',
              teacher_name: '',
          },
          time_table: [
              { "time_table_id": "", "time": "08:00:00", "term": "2", "day": "MON", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" ,"school_year":""},
              { "time_table_id": "", "time": "09:00:00", "term": "2", "day": "MON", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "10:00:00", "term": "2", "day": "MON", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "11:00:00", "term": "2", "day": "MON", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "13:00:00", "term": "2", "day": "MON", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "14:00:00", "term": "2", "day": "MON", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "15:00:00", "term": "2", "day": "MON", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },

              { "time_table_id": "", "time": "08:00:00", "term": "2", "day": "TUE", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "09:00:00", "term": "2", "day": "TUE", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "10:00:00", "term": "2", "day": "TUE", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "11:00:00", "term": "2", "day": "TUE", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "13:00:00", "term": "2", "day": "TUE", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "14:00:00", "term": "2", "day": "TUE", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "15:00:00", "term": "2", "day": "TUE", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },

              { "time_table_id": "", "time": "08:00:00", "term": "2", "day": "WED", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "09:00:00", "term": "2", "day": "WED", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "10:00:00", "term": "2", "day": "WED", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "11:00:00", "term": "2", "day": "WED", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "13:00:00", "term": "2", "day": "WED", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "14:00:00", "term": "2", "day": "WED", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "15:00:00", "term": "2", "day": "WED", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },

              { "time_table_id": "", "time": "08:00:00", "term": "2", "day": "THU", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "09:00:00", "term": "2", "day": "THU", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "10:00:00", "term": "2", "day": "THU", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "11:00:00", "term": "2", "day": "THU", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "13:00:00", "term": "2", "day": "THU", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "14:00:00", "term": "2", "day": "THU", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "15:00:00", "term": "2", "day": "THU", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },

              { "time_table_id": "", "time": "08:00:00", "term": "2", "day": "FRI", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "09:00:00", "term": "2", "day": "FRI", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "10:00:00", "term": "2", "day": "FRI", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "11:00:00", "term": "2", "day": "FRI", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "13:00:00", "term": "2", "day": "FRI", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "14:00:00", "term": "2", "day": "FRI", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
              { "time_table_id": "", "time": "15:00:00", "term": "2", "day": "FRI", "teacher_id": "", "subject_id": "", "subject_name": "", "first_name": "", "last_name": "", "enroll_subject_id": "" },
             ]
      }
  },
//    beforeCreate() {
        
//        axios.get('http:localhost/service_ip3/teacher/schedule.php',{params: 
//                {id: this.teacher_id}
//            })
//            .then((resp) => {
//                 this.time_table = resp.data.response
//                for (const i in this.time_table){
//                    for (const x in resp.data.response){
//                        if (this.time_table[i].day === resp.data.response[x].day && this.time_table[i].time === resp.data.response[x].time){
//                            this.time_table[i] = resp.data.response[x]
//                        }
//                    };
//                }
//                  console.log(resp.data) // eslint-disable-next-line no-console
//            })
//        for(const i in this.time_table){
//            this.time_table[i] = (Object.assign(this.time_table[i], { "school_year": this.data_form.school_year, "grade": this.data_form.grade, "room": this.data_form.room }));
//        }    
       
//    },
//   created() {
//     this.storage();
//       axios.get('http://localhost/service_ip3/teacher/schedule.php',
//           {params: 
//               {id: this.teacher_id}
//           })
//           .then((resp) => {
//               // this.time_table = resp.data.response
//               for (const i in this.time_table){
//                   for (const x in resp.data.response){
//                       if (this.time_table[i].day === resp.data.response[x].day && this.time_table[i].time === resp.data.response[x].time){
//                           this.time_table[i] = resp.data.response[x]
//                       }
//                   };
//               }
//           })
//         console.log(sessionStorage.getItem('user_id'))
//   },
  mounted() {
    this.storage();
      axios.get('http://localhost/service_ip3/student/schedule.php',
          {params: 
              {id: this.student_id}
          })
          .then((resp) => {
              // this.time_table = resp.data.response
              for (const i in this.time_table){
                  for (const x in resp.data.response){
                      if (this.time_table[i].day === resp.data.response[x].day && this.time_table[i].time === resp.data.response[x].time){
                          this.time_table[i] = resp.data.response[x] 
                          
                      }
                  };
              }
             
          })
        // console.log(this.data_form) // eslint-disable-next-line no-console
  },
//   updated() {
//       axios.get('http://localhost/service_ip3/teacher/schedule.php',{params: 
//               {id: sessionStorage.getItem('user_id')}
//           })
//           .then((resp) => {
//               // this.time_table = resp.data.response
//               for (const i in this.time_table){
//                   for (const x in resp.data.response){
//                       if (this.time_table[i].day === resp.data.response[x].day && this.time_table[i].time === resp.data.response[x].time){
//                           this.time_table[i] = resp.data.response[x]
//                       }
//                   };
//               }
//           })
//       for(const i in this.time_table){
//           this.time_table[i] = (Object.assign(this.time_table[i], { "school_year": this.data_form.school_year, "grade": this.data_form.grade, "room": this.data_form.room }));
//       }
//       // console.log(this.time_table);
      
//   },
  methods: {
      get_subject_name(){
          this.data_form.subject_name = ''
          axios.get('http://localhost/service_ip3/student/showSubject.php',
          {params :{id: this.data_form.subject_id}})
          .then((resp) => {
                  this.data_form.subject_name = resp.data.response[0].subject_name
              })
      },
      get_teacher_name(){
          this.data_form.teacher_name = ''
          axios.get('http://localhost/service_ip3/teacher/info.php',
          {params :{id: this.data_form.teacher_id}})
          .then((resp) => {
                  this.data_form.teacher_name = resp.data.response[0].first_name + "  " + resp.data.response[0].last_name
              }) 
      },
      
      handle(index) {
          this.status_form.index = index
          this.status_form.expansion = !this.status_form.expansion
          this.data_form.subject_id = this.time_table[index].subject_id
          this.data_form.subject_name = this.time_table[index].subject_name
          this.data_form.teacher_id = this.time_table[index].teacher_id
          this.data_form.teacher_name = this.time_table[index].first_name + "  " + this.time_table[index].last_name
          this.get_teacher_name()
      },
      // get_subject() {
      //     axios.get('http://localhost/service_ip3/admin/enroll_subject/get_subject_by_class.php',
      //     {params: 
      //         {school_year: this.data_form.school_year,
      //         grade: this.data_form.grade,
      //         room: this.data_form.room,}
      //     })
      //         // .then((resp) => {
      //         //     console.log(resp.status);
      //         // })
      // },
      storage(){
            this.student_id = sessionStorage.getItem('user_id')
      }  
  },
}
</script>
<style lang="">
  
</style>