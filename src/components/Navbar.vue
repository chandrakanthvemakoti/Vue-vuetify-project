<template>
<nav>
  <v-toolbar  dark flat app color="indigo">
    <v-toolbar-title>
        <span>VUE JS PROJECT</span>
    </v-toolbar-title>
    <v-spacer></v-spacer>
    <v-btn flat color="indigo">
        <router-link to="/register" style="color:white;text-decoration:none"><span>Sign Up</span></router-link>
    </v-btn>
    <v-btn flat color="indigo">
        <router-link to="/login" style="color:white;text-decoration:none"><span>Sign In</span></router-link>
    </v-btn>
    <v-btn flat color="indigo">
        <span>Dashboard</span>
    </v-btn>
  </v-toolbar>

  </nav>
</template>

<script>
export default {
    data(){
        return{
            drawer:false
        }
    }
}
</script>