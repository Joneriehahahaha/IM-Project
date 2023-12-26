<script setup>

    import {ref} from 'vue'
    const auth = ref(null)
    auth.value = JSON.parse(localStorage.getItem('auth'))

    function logout() {
        localStorage.removeItem('auth')
        auth.value = null
    }

</script>
<template>
    <v-layout>
        <v-app-bar color="teal-darken-4" image="https://images.unsplash.com/photo-1578997864329-d747473f7359?q=80&w=1000&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Nnx8ZGFyayUyMGFlc3RoZXRpY3xlbnwwfHwwfHx8MA%3D%3D">
            <template v-slot:image>
                <v-img gradient="https://images.unsplash.com/photo-1578997864329-d747473f7359?q=80&w=1000&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Nnx8ZGFyayUyMGFlc3RoZXRpY3xlbnwwfHwwfHx8MA%3D%3D"></v-img>
            </template>
            <v-app-bar-title style="color: black;">Account Management</v-app-bar-title>
            <v-spacer></v-spacer>
            <div v-if="auth">
                <router-link to="/">
                    <v-btn color="black">
                        Events
                    </v-btn>
                </router-link>
                <router-link to="/account">
                    <v-btn color="black">
                        Account
                    </v-btn>
                </router-link>
                <router-link to="/sign-in">
                    <v-btn color="red" @click="logout">
                        Logout
                    </v-btn>
                </router-link>
            </div>
            <div v-else>
                <router-link to="/sign-in">
                    <v-btn color="white">
                        Sign in
                    </v-btn>
                </router-link>
                <router-link to="/sign-up">
                    <v-btn color="white">
                        Sign up
                    </v-btn>
                </router-link>
            </div>
        </v-app-bar>

        <v-main class="bg-grey-darken-3">
            <v-container>
                <slot/>
            </v-container>
        </v-main>
    </v-layout>
</template>

<style scoped>
    .link {
        text-decoration: none;
    }
</style>
