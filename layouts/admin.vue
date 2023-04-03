<template>
    <v-app>
        <v-layout row wrap>
            <v-navigation-drawer permanent expand-on-hover>
                <v-list>
                    <v-list-item class="px-2">
                        <v-list-item-avatar>
                            <v-img src="https://randomuser.me/api/portraits/women/85.jpg"></v-img>
                        </v-list-item-avatar>
                    </v-list-item>

                    <v-list-item link>
                        <v-list-item-content>
                            <v-list-item-title class="text-h6">
                                Admin
                            </v-list-item-title>
                        </v-list-item-content>
                    </v-list-item>
                </v-list>
                <v-divider>
                </v-divider>

                <v-list v-for="(item, i) in items" :key="i" dense nav>
                    <v-list-item link :to="item.to" router exact>
                        <v-list-item-icon>
                            <v-icon>{{ item.icon }}</v-icon>
                        </v-list-item-icon>
                        <v-list-item-title>{{ item.title }}</v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-navigation-drawer>
            <v-main style="height: 500px;">
                <v-card-text class="pa-12">
                    <nuxt />
                </v-card-text>
            </v-main>
        </v-layout>
    </v-app>
</template>
<script>
export default {
    data() {
        return {
            items: [
                {
                    icon: 'mdi-account-multiple',
                    title: 'Student',
                    to: '/admin/student',
                },
                {
                    icon: 'mdi-account-multiple',
                    title: 'Teacher',
                    to: '/admin/teacher',
                },
                {
                    icon: 'mdi-folder',
                    title: 'Schedule',
                    to: '/admin/subject',
                },
                {
                    icon: 'mdi-account-multiple',
                    title: 'Advicers',
                    to: '/admin/advicers',
                },
                {
                    icon: 'mdi-folder',
                    title: 'Enroll Subject',
                    to: '/admin/enroll_subject',
                },
            ],
        }
    }

}
</script>