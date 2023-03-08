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
                        <v-avatar color="brown" size="48">
                            <span class="white--text text-h5">{{ user.initials }}</span>
                        </v-avatar>
                    </v-btn>
                </template>
                <v-card>
                    <v-list-item-content class="justify-center">
                        <div class="mx-auto text-center">
                            <v-avatar color="brown">
                                <span class="white--text text-h5">{{ user.initials }}</span>
                            </v-avatar>
                            <h3>{{ user.fullName }}</h3>
                            <v-divider class="my-3"></v-divider>
                            <v-tabs>
                                <v-tab v-for="(item, link) in linkss" :key="link" :to="item.to">
                                    {{ item.title }}
                                </v-tab>
                            </v-tabs>
                            
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
import Info from '../components/showInfo.vue'
import Work from '../components/showWork.vue'
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
                to: '/student/schedule',
            }
        ],
        linkss: [
            {
                title: 'Score',
                to: '/student/score',
            },
            {
                title: 'Grade',
                to: '/student/grade',
            },
            {
                title: 'Classmate',
                to: '/student/classmate',
            }
        ],
        user: {
            initials: 'Jt',
            fullName: 'John Doe',
        },
    }),
    mounted() {
        this.checkLogin();
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
        }
    },
    
}
</script>
