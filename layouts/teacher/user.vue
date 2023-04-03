<template>
    <v-app id="inspire">
        <v-app-bar flat>
            <!-- <v-avatar :color="$vuetify.breakpoint.smAndDown ? 'grey darken-1' : 'transparent'" size="32"></v-avatar> -->
            <v-tabs centered class="ml-9" color="grey darken-1">
                <v-tab v-for="(item, link) in links" :key="link" :to="item.to">
                    {{ item.title }}
                </v-tab>
            </v-tabs>

            <v-menu bottom min-width="200px" rounded offset-y>
                <template #activator="{ on }">
                    <v-btn icon x-large v-on="on">
                        <v-avatar color="brown" size="48"></v-avatar>
                    </v-btn>
                </template>
                <v-card>
                    <v-list-item-content class="justify-center">
                        <div class="mx-auto text-center">
                            <v-avatar color="brown"></v-avatar>
                            <h3>{{ tea[0].fist_name}}&nbsp;{{ tea[0].last_name }}</h3>
                            <v-divider class="my-3"></v-divider>
                            <v-btn depressed text to="/teacher/score">
                                Score
                            </v-btn>
                            <v-divider class="my-3"></v-divider>
                            <v-btn depressed text to="/teacher/grade">
                                Grade
                            </v-btn>
                            <v-divider class="my-3"></v-divider>
                            <v-btn depressed text to="/teacher/classmate">
                                Classmate
                            </v-btn>
                            <v-divider class="my-3"></v-divider>
                            <v-btn @click="hendleLogout()">
                                <v-icon>mdi-logout</v-icon>
                                Logout
                            </v-btn>
                        </div>
                    </v-list-item-content>
                </v-card>
            </v-menu>
            <div class="hidden-sm-and-down"></div>
        </v-app-bar>
        <v-main>
            <v-container>
                <v-row>
                    <v-col cols="12" sm="2">
                        <v-card rounded="lg" min-height="268">
                            <!--  -->
                            <Work/>
                        </v-card>
                    </v-col>

                    <v-col cols="12" sm="8">
                        <v-card min-height="70vh" rounded="lg">
                            <nuxt></nuxt>
                        </v-card>
                    </v-col>

                    <v-col cols="12" sm="2">
                        <v-card rounded="lg" min-height="268">
                            <!--  -->
                            <Info />
                        </v-card>
                    </v-col>
                </v-row>
            </v-container>
        </v-main>
    </v-app>
</template>
  
<script>
import axios from 'axios'
import Info from '../../components/teacher/showInfo.vue'
import Work from '../../components/teacher/showWork.vue'

export default {
    components: {
        Work, 
        Info 
    },
    data: () => ({
        links: [
            {
                title: 'home',
                to: '/',
            },
            {
                title: 'schedule',
                to: '/teacher/schedule',
            }
        ],
        teacher_id:'',
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
        this.checkLogin();
        this.storage();
        axios.get('http://localhost/service_ip3/teacher/info.php',{params: {id:this.teacher_id}})
        .then((resp) => {
            this.tea = resp.data.response
        })
    },
    methods: {
        hendleLogout() {
            sessionStorage.clear()
            window.location = './login'
        },
        checkLogin() {
            if(!sessionStorage.getItem('user_id')){
                window.location = './login'
            } 
        },
        storage(){
            this.teacher_id = sessionStorage.getItem('user_id')
        }   
    },
    
}
</script>
