<template>
  <v-container>
    <h1>Form</h1>
  <form>
    <v-text-field
      v-model="name"
      :error-messages="nameErrors"
      label="Name"
      required
      @input="$v.name.$touch()"
      @blur="$v.name.$touch()"
    ></v-text-field>
    <v-text-field
      v-model="email"
      :error-messages="emailErrors"
      label="Email"
      type="email"
      required
      @input="$v.email.$touch()"
      @blur="$v.email.$touch()"
    ></v-text-field>
   <v-select
   :items="items"
    v-model="role"
    label="Role"
    required 
    @change="$v.role.$touch()"
    @blur="$v.role.$touch()"
    :error-messages="roleErrors">
   

   </v-select>
    <v-btn @click="submit"
    :disabled="$v.$invalid"
     >Submit</v-btn>
    <v-btn @click="clear">
        Clear
    </v-btn>
  </form></v-container>

</template>
<script>

import {required,email} from 'vuelidate/lib/validators'
export default {

  data(){
    return{
        id:null,
      name:'',
      email:'',
      role:'',
      items:[
          'java developer',
          'vue developer',
          'react developer',
          'node developer'
      ],
      employee:[]
    }

   
  },
  mounted(){
  this.id=this._uid
  },
   computed: {

     nameErrors() {
       const errors =[]
       if(!this.$v.name.$dirty) return errors
       !this.$v.name.required && errors.push('please enter the name')
       return errors
       
     },
     emailErrors(){
       const errors = []
       if(!this.$v.email.$dirty) return errors
       !this.$v.email.required && errors.push('please enter the email')
       !this.$v.email.email && errors.push('please enter valid mail id')
       return errors
       

     },
     roleErrors(){
         const errors = []
         if(!this.$v.role.$dirty) return errors
         !this.$v.role.required && errors.push("please select the role")
         return errors
     }
      
    },
    validations:{
   name:{required},
   email:{required,email},
   role:{required}
    },
    methods:{
      submit: function(e){
          e.preventDefault();
          var obj={
              name:this.name,
              email:this.email,
              role:this.role
          };
          this.employee.push(obj);
          this.$emit('myemit',this.employee);
          this.name='';
          this.email='';
          this.role='';
         

        
      },

      clear(){

   this.$v.$reset()
   this.name=''
   this.email=''
   this.role=''

}
    }
  
}
</script>
