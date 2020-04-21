<template>
<nav>
  <v-toolbar  dark flat app color="indigo">
    <v-toolbar-title>
        <span>VUE JS PROJECT</span>
    </v-toolbar-title>
    <v-spacer></v-spacer>
    <v-btn flat color="indigo">
        <span>Sign In</span>
    </v-btn>
    <v-btn flat color="indigo">
        <span>Sign Up</span>
    </v-btn>
    <v-btn flat color="indigo">
        <span>Dashboard</span>
    </v-btn>
  </v-toolbar>
  <v-navigation-drawer app v-model="drawer" dark> 
  hello
  </v-navigation-drawer>
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