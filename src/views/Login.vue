<template>
  <v-container>
    <h1>LOGIN</h1>
  <form>
    <v-text-field
      v-model="username"
      :error-messages="usernameErrors"
      :counter="10"
      label="Username"
      required
      @input="$v.username.$touch()"
      @blur="$v.username.$touch()"
    ></v-text-field>
    <v-text-field
      v-model="password"
      :error-messages="passwordErrors"
      label="Password"
      type="password"
      required
      @input="$v.password.$touch()"
      @blur="$v.password.$touch()"
    ></v-text-field>
    <v-btn @click="submit">Submit</v-btn>
  </form></v-container>

</template>
<script>

import {required} from 'vuelidate/lib/validators'
export default {

  data(){
    return{
      username:'',
      password:''
    }

   
  },
   computed: {

     usernameErrors() {
       const errors =[]
       if(!this.$v.username.$dirty) return errors
       !this.$v.username.required && errors.push('please enter the username')
       return errors
       
     },
     passwordErrors(){
       const errors =[]
       if(!this.$v.password.$dirty) return errors
       !this.$v.password.required && errors.push('please enter the password')
       return errors
       

     }
      
    },
    validations:{
   username:{required},
   password:{required}
    },
    methods:{
      submit(){
        this.$v.$touch()
        this.$router.push({name:'dashboard'})
      }
    }
  
}
</script>
