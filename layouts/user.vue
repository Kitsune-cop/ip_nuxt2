<template>
    <v-app id="inspire">
        <v-app-bar flat>
            <v-avatar :color="$vuetify.breakpoint.smAndDown ? 'grey darken-1' : 'transparent'" size="32"></v-avatar>
            <v-tabs centered class="ml-n9" color="grey darken-1">
                <v-tab v-for="(item, link) in links" :key="link" :to="item.to">
                    {{ item.title }}
                </v-tab>
            </v-tabs>

            <v-menu bottom min-width="200px" rounded offset-y>
                <template v-slot:activator="{ on }">
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
                            <p class="text-caption mt-1">
                                {{ user.email }}
                            </p>
                            <v-divider class="my-3"></v-divider>
                            <v-btn @click="hendleLogout()">
                                <v-icon>mdi-logout</v-icon>
                                Logout
                            </v-btn>
                        </div>
                    </v-list-item-content>
                </v-card>
            </v-menu>
            <div class="mx-3 hidden-sm-and-down"></div>
            <!-- <v-btn icon mdi-account-circle>
                <v-avatar class="hidden-sm-and-down" color="grey darken-1 shrink" size="32"></v-avatar>
            </v-btn> -->
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
                            <!--  -->
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
import Info from '../components/info.vue'
import Work from '../components/work.vue'
export default {
    data: () => ({
        links: [
            {
                title: 'home',
                to: '/',
            },
            {
                title: 'info',
                to: '/info',
            },
            {
                title: 'schedule',
                to: '/schedule',
            }
        ],
        user: {
            initials: 'Jt',
            fullName: 'John Doe',
            email: 'john.doe@doe.com',
        },
    }),
    components: {
        Work, 
        Info 
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
    mounted() {
        this.checkLogin();
    }
}
</script>
